## Container Scanning using GitLab
============================================

Container scanning in GitLab is an important practice for ensuring that your containerized applications are secure. 

GitLab provides tools for scanning Docker images for known vulnerabilities and other security issues.

By setting up container scanning in GitLab, you can ensure that your Docker images are secure and free from known vulnerabilities. 

Integrating it into your CI/CD pipeline is straightforward, and GitLab provides an automated way to track and mitigate vulnerabilities as part of the development process.

#### 1. Enable Container Scanning in GitLab CI/CD

GitLab uses the Container Scanning feature as part of its built-in security scanning tools. 

This is done through GitLab CI/CD pipelines. 

To enable container scanning in your pipeline, you need to add the appropriate configuration in the `.gitlab-ci.yml file`.

`Steps`

A. Create or update your .gitlab-ci.yml file.

B. Add the container_scanning job to your pipeline configuration. The job will automatically scan your Docker image for vulnerabilities when it runs.

```
stages:
  - build
  - test
  - container_scan
  - deploy

container_scan:
  stage: container_scan
  image: docker:latest
  script:
    - docker build -t myimage .
    - docker push myimage
  allow_failure: true
  artifacts:
    reports:
      container_scanning: gl-container-scanning-report.json
```


In the above example, we have a container_scan job that runs after the build and test stages.

The docker image is used in the job to build the container image (docker build -t myimage .) and then push it to a container registry.

#### 2. GitLab Container Scanning Features

GitLab uses the GitLab Container Scanning feature to scan Docker images for vulnerabilities. This is powered by Trivy (an open-source vulnerability scanner).

GitLab checks the security of both the base image and the application dependencies in your Dockerfile.

It identifies vulnerabilities listed in multiple databases like NVD, Red Hat CVE database, etc.

GitLab creates a report in the pipeline, so you can review and address vulnerabilities.

#### 3. Reviewing the Scan Results 

After the container scanning job runs, GitLab generates a detailed report of the security vulnerabilities found in the Docker image. 

You can view the results from :-

`Merge request` GitLab will show security scan results directly in the merge request.

`Pipeline view` Results are also available in the pipeline’s job output.

You can view the security vulnerabilities, categorized by severity (Low, Medium, High, Critical), and take action to resolve them.

#### 4. Configure Vulnerability Management

GitLab provides integrated vulnerability management tools, so once vulnerabilities are found, you can track and manage them within GitLab:

You can integrate with GitLab’s Security Dashboard to get an overview of all detected vulnerabilities.

GitLab allows you to set policies to block merging of code that introduces vulnerabilities.

#### 5. Running Container Scanning on Self-Hosted GitLab

If you're running GitLab on your own infrastructure (self-hosted), you need to ensure that you have the appropriate GitLab Runner installed and configured to use container scanning features. 

This typically involves ensuring the runner is capable of running Docker commands and has access to Docker images.

#### 6. Allow Failure

In the .gitlab-ci.yml file, you can configure the container scanning job to allow failure, meaning the pipeline will continue even if vulnerabilities are found.

This might be useful during development, but for production, it's recommended to fail the job if vulnerabilities are detected.

```
allow_failure: false
```

#### 7. Additional Scanning with Other Tools

If you'd like to perform additional scanning beyond container scanning, GitLab integrates with tools like :-

  - SAST (Static Application Security Testing): For source code analysis.
  - DAST (Dynamic Application Security Testing): For runtime analysis of web applications.

