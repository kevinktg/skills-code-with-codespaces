on:
  push:
    branches:
      - main

jobs:
  on_add_dependency:
    name: On Add dependency
    if: >-
      ${{ !github.event.repository.is_template }}

    runs-on: ubuntu-latest

    env: # Add your environment variables here
      FILE: "index.html"
      SEARCH: "Hello from the codespace"
      FROM_STEP: "1"
      TO_STEP: "2"
      GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }} # Ensure this is set in your repository secrets

    steps:
      - name: Checkout
        uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Check workflow contents, jobs
        uses: skills/action-check-file@v1
        with:
          file: ${{ env.FILE }}
          search: ${{ env.SEARCH }}

      - name: Update to step 2
        uses: skills/action-update-step@v2
        with:
          token: ${{ env.GITHUB_TOKEN }}
          from_step: ${{ env.FROM_STEP }}
          to_step: ${{ env.TO_STEP }}