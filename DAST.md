## What is DAST ?
========================

DAST stands for Dynamic Application Security Testing.

It is a type of black-box security testing that analyzes web applications in their running state to find security vulnerabilities.

Unlike static testing (which inspects source code), DAST tests the application from the outside.



## Configuring DAST with GitLab
======================================

Configuring DAST with GitLab involves setting up GitLab CI/CD to automatically run security scans against your running application. 

GitLab provides a built-in DAST template that makes this relatively straightforward.

#### Prerequisites

GitLab Premium or Ultimate (DAST is available in higher tiers).

A web application deployed to a test/staging environment accessible from the GitLab Runner.

The application must be running when the DAST job executes.


`Step-by-Step`

Add a .gitlab-ci.yml File or Modify It

```
stages:
  - test

dast:
  stage: test
  image: registry.gitlab.com/gitlab-org/security-products/dast
  script:
    - /analyze
  variables:
    DAST_WEBSITE: "https://your-staging-site.com"  # Replace with your app's URL
    DAST_FULL_SCAN_ENABLED: "true"  # Optional, enables a full scan

```

Push your changes to GitLab, and the pipeline will start. The DAST job will run and scan the live app.


Once the pipeline finishes :-

Navigate to Security > Vulnerability Report in your GitLab project.

You'll see a list of issues found by DAST with severity and remediation advice.

