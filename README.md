# packj-npm-registry-firewall-action
Packj firewall for NPM registry

*Note* you will have to create an account on https://packj.dev and obtain an authentication token.

## Inputs

- PACKJ_FIREWALL_TOKEN: auth token

## Example use

```yaml
# This is a basic workflow to help you get started with Actions
name: Packj NPM Registry Firewall Demo

# Controls when the workflow will run
on:
  pull_request:
    branches:
      - main

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:

  # This workflow contains a single job called "packj-audit"
  packj-npm-registry-firewall:

    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:

      # Setup Packj NPM Firewall by using this Github action
      - name: Setup Packj NPM registry firewall
        uses: ossillate-inc/packj-npm-registry-firewall-action@v0.0.1-beta
        with:
          PACKJ_FIREWALL_TOKEN: ${{ secrets.PACKJ_FIREWALL_TOKEN }}

      # Checkout target project repo
      - name: Checkout repo
        uses: actions/checkout@v2

      # Now safely install all project dependencies
      - name: Install dependencies
        run: npm install
        shell: bash
```
