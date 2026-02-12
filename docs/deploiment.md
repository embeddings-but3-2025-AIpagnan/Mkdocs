Le projet dispose d'une pipeline CD qui permet de build automatiquement l'application pour Linux, Windows et MacOS et de publier la release dès qu'un tag de version est poussé sur Github, ou sur intervention manuelle.

Voici le fichier de CD commenté:
```yml
name: publish

# Quand es-ce que le CD s'active
on:
  push:
    tags:
      # Tag de version
      - 'v*.*.*'
  # Activation manuelle
  workflow_dispatch:

jobs:
  build:
    permissions:
      contents: write

    strategy:
      fail-fast: false
      # Toutes les plateformes sur lesquelles build
      matrix:
        include:
          - platform: ubuntu-latest
          - platform: macos-latest
          - platform: windows-latest
    runs-on: ${{ matrix.platform }}

    steps:
      # Cloner le repo
      - uses: actions/checkout@v4

      # Installation de node (version lts)
      - name: setup node
        uses: actions/setup-node@v4
        with:
          node-version: lts/*

      # Installation de Python et des dépendances python du projet
      - name: setup python
        uses: actions/setup-python@v6
        with:
          python-version: '3.13'
          cache: 'pip'
          cache-dependency-path: backend/requirements.txt
      - run: pip install -r backend/requirements.txt

      # Installation de Rust
      - name: install Rust stable
        uses: dtolnay/rust-toolchain@stable

     # Installation des dépendances natives de Tauri (sur ubuntu uniquement)
      - name: install dependencies (ubuntu only)
        if: matrix.platform == 'ubuntu-latest'
        run: |
          sudo apt-get update
          sudo apt-get install -y libwebkit2gtk-4.1-dev libappindicator3-dev librsvg2-dev patchelf

      # Installation des dépendances javascript
      - name: install frontend dependencies
        run: npm install

      # Build du backend (compilation du python en un exécutable autonome)
      - name: build backend
        run: npm run build:backend

      # Sign that new executable
      - name: sign backend binary (macos only)
        if: matrix.platform == 'macos-latest'
        run: |
          for bin in build/dist/backend-*; do
            if [[ -f "$bin" && ! -L "$bin" ]]; then
              codesign --force --deep --sign - "$bin"
            fi
          done

      # Build the frontend (astro)
      - name: build frontend
        run: npm run build:frontend

      # Build et publish le projet final grâce à une action préfaite de Tauri
      - uses: tauri-apps/tauri-action@v0.6
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          tagName: app-v__VERSION__
          releaseName: 'GlossAI v__VERSION__'
          releaseDraft: false
          prerelease: false
```