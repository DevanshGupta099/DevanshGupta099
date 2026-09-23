name: Generate Snake Animation
on:
  schedule:
    - cron: "0 */12 * * *"   # runs every 12 hours
  workflow_dispatch:          # lets you trigger it manually from the Actions tab

permissions:
  contents: write            # lets the job push the generated files to the "output" branch

jobs:
  build:
    name: Generate contribution snake
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repo
        uses: actions/checkout@v4

      - name: Generate snake animation (light + dark)
        uses: Platane/snk@v3
        id: snake-gif
        with:
          github_user_name: DevanshGupta099
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - name: Push output to "output" branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
