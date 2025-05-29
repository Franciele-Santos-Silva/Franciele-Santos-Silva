#Olá! eu sou a Franciele Santos Silva

🔭 Trabalhando em projetos de IA, focando em assistentes virtuais e machine learning.

🌱 Aprendendo Python avançado, ML, Deep Learning, NLP.

👯 Buscando colaborar em projetos de IA e assistentes virtuais.

🤔 Procurando ajuda com deploy de modelos.

💬 Pergunte-me sobre IA, assistentes virtuais e Python.

😄 Pronomes: ela/dela.

name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}


