name: Generate Snake

on:
  schedule:
    - cron: "0 */12 * * *"
  workflow_dispatch:
  push:
    branches:
      - main

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - uses: Platane/snk/svg-only@v3
        with:
          github_user_name: SheetalNaik98
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
            
      - uses: EndBug/add-and-commit@v9
        with:
          branch: output
          message: 'Generate snake'
          add: 'dist/*.svg'
