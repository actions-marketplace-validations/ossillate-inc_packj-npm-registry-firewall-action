# packj-npm-registry-firewall-action
Packj firewall for NPM registry will block the installation of any vulnerable, abandonded, typo-squatted, and ESLint-like malicious NPM dependency.

The screenshot below depcits how Packj Firewall in action. 

<img src="https://packj.dev/static/img/example.svg" style="width:40%;height:40%;float:center;"></img>

Simply, add the following snippet to your workflow (first step, before installing any NPM dependencies)

```yaml
# Setup Packj NPM Firewall by using this Github action    
- name: Setup Packj NPM registry firewall
uses: ossillate-inc/packj-npm-registry-firewall-action@v0.0.1-beta
with:
  PACKJ_FIREWALL_TOKEN: ${{ secrets.PACKJ_FIREWALL_TOKEN }}
```

## Inputs

- PACKJ_FIREWALL_TOKEN: auth token

*Note* you will have to create an account on https://packj.dev and obtain an authentication token.

## Detailed example usage

```yaml
# This is a basic workflow to help you get started with Actions
name: Packj NPM Registry Firewall

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
