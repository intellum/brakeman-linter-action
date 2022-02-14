## Brakeman github action

Forked from devmasx, because github actions can only use github-approved actions or those from the same org.

Brakeman is a static analysis tool which checks Ruby on Rails applications for security vulnerabilities.
[See more](https://github.com/presidentbeef/brakeman)

### Usage

```yml
- name: Brakeman
  uses: intellum/brakeman-linter-action@v1.0.0
  env:
    GITHUB_TOKEN: ${{secrets.GITHUB_TOKEN}}
```

### Custom report

```yml
- name: Install gems
  run: |
    gem install brakeman -v 4.5.0
- name: brakeman report
  run: |
    brakeman -f json > tmp/brakeman.json || exit 0
- name: Brakeman
  uses: intellum/brakeman-linter-action@v1.0.0
  env:
    GITHUB_TOKEN: ${{secrets.GITHUB_TOKEN}}
    REPORT_PATH: tmp/brakeman.json
```

### Custom path

```yml
- name: Brakeman
  uses: intellum/brakeman-linter-action@v1.0.0
  env:
    GITHUB_TOKEN: ${{secrets.GITHUB_TOKEN}}
    PROJECT_PATH: my_rails_app
```

### Example Workflow

```
name: Brakeman

on: [push]

jobs:
  build:
    runs-on: ubuntu-18.04
    steps:
    - uses: actions/checkout@v1
    - name: Brakeman
      uses: intellum/brakeman-linter-action@v1.0.0
      env:
        GITHUB_TOKEN: ${{secrets.GITHUB_TOKEN}}
```

## Screenshots

![example GitHub Action UI](./screenshots/action.png)
![example Pull request](./screenshots/pull_request.png)
