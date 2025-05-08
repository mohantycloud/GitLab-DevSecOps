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
