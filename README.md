# Usage

Dependency auditor is best used as part of your CI / CD pipeline.


## Gitlab CI

In your `.gitlab-ci.yml` file:

```
dependency_auditor:
  image: python:3
  script:
    - apt-get install -y wget
    - wget https://raw.githubusercontent.com/matix-io/dependency-auditor/master/dependency-auditor
    - DA_PYTHON_REQUIREMENTS_FILE=$(pwd)/requirements.txt /bin/sh $(pwd)/dependency-auditor
  only:
    - master
    - schedules
```

We recommend setting up Gitlab Schedules to run the auditor at some regular interval, so that you'll learn about vulnerabilities even if you aren't deploying.

