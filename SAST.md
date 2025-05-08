## What is SAST ?
========================


Static Application Security Testing (SAST) in GitLab is a built-in feature that automatically scans your source code for security vulnerabilities. 

It’s part of GitLab’s Secure stage and helps developers catch security issues early in the development lifecycle, directly within the CI/CD pipeline.

It is a type of security testing that analyzes your source code, bytecode, or binary code for vulnerabilities without executing the application.

#### Key Features of GitLab SAST

`Language support` Works with many popular languages like Python, JavaScript, Java, Ruby, Go, C/C++, PHP, etc.

`Automatic setup` GitLab can auto-detect the programming language and set up SAST scanners.

`CI/CD integration` Scans are triggered via .gitlab-ci.yml during merge requests or pipeline runs.

`Reports and merge request feedback` Vulnerabilities are reported in the pipeline and directly in merge requests.

`Customizable` You can enable/disable specific analyzers or configure rules via custom YAML configuration.


## GitLab SAST integration
===============================

Integrating GitLab Static Application Security Testing (SAST) into your CI/CD pipeline helps automatically scan your code for security vulnerabilities. 

GitLab provides built-in support for SAST using CI templates and supports many languages and frameworks out-of-the-box.

#### Steps to Integrate GitLab SAST

1. Auto-DevOps (Automatic Setup) > If Auto DevOps is enabled and your project uses a supported language, GitLab automatically runs SAST.

2. Manual Setup with `.gitlab-ci.yml`

```
include:
  - template: Security/SAST.gitlab-ci.yml
```

After the pipeline runs, navigate to Security & Compliance > Vulnerability Report in your GitLab project.

Each vulnerability includes :-

  - File and line number
  - Suggested fix (if available)
  - CVE/CWE references





