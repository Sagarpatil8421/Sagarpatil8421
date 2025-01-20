name: Update README

on:
  schedule:
    - cron: '0 0 * * *' # Runs daily at midnight
  workflow_dispatch:

jobs:
  update-readme:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v3

      - name: Fetch Stats and Update README
        run: |
          python script.py # Run your script here
      - name: Commit and Push Changes
        run: |
          git config --global user.name 'GitHub Actions'
          git config --global user.email 'actions@github.com'
          git add README.md
          git commit -m "Updated dynamic data in README"
          git push
