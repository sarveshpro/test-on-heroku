# test-on-heroku

# Usage

In order to use the action in your workflow, just add in your _.github/workflows/YOURACTION.yml_

```yaml
name: Test Heroku

on:
  push:
    branches:
      - ${{secrets.BRANCH_TO_TEST}}

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: akhileshns/heroku-deploy@v3.0.4 # This is the action
        with:
          heroku_api_key: ${{secrets.HEROKU_API_KEY}}
          heroku_app_name: ${{secrets.HEROKU_APP_NAME}}  #Must be unique in Heroku
          heroku_email: ${{secrets.HEROKU_EMAIL}}
          buildpack: ${{secrets.BUILDPACK}}
          branch: ${{secrets.BRANCH_TO_TEST}}
          dontuseforce: false #OPTIONAL and DEFAULT - false
          usedocker: false #OPTIONAL and DEFAULT - false
          appdir: "" #OPTIONAL and DEFAULT - "". This is useful if the api you're deploying is in a subfolder
          docker_heroku_process_type: "" #OPTIONAL and DEFAULT - "web"
```
