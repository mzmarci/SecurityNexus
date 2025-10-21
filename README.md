# SecurityNexus

## Project Architecture

This is a devsecops project, this is a cloned vulerable application that will help in implementing DevSecOps .
In DevSecOps we are SHIFTING SECUIRTY LEFT and this means that we are moving the secuirty as close to the developer as possible

## Benefits of the Shift Left Security
1. Early Detection: We are able to detect a problem before it gets out to production

2. Cost Savings: Detecting a software vulnerability earlier in the software life cycle it's going to be a lot more cost effective to squash that bug to fix that secuirty vulnerability that it would be to patch it when its out in production.

## How to implement 

1. Started with running my application locally using docker compose.

2. After i started the application, i ran docker scout, in the docker scout the one am looking into is the (cves - Display CVEs identified in a software artifact) this stands for Common Vulnerabilties and Exposures. so if you want to check ur docker images for vulnerability you use the docker scout command.

Now the next thing to run on your command line is Docker scout cves (your image name), this shows you all the vulnerabilites in your container image

##  Moving to CI/CD using Github actions

3. Gitleaks: is an open-source tool that detects hardcoded secrets (like AWS keys, passwords, tokens) in your repo. It helps prevent accidentally exposing sensitive data in GitHub. You can run it manually or automatically as part of your CI/CD pipeline (e.g., GitHub Actions).

What happens

✅ Every time you push or open a pull request:

GitHub Actions runs Gitleaks

Scans your code for secrets

If secrets are found, the job fails and prints a report in the logs (or you can download the report as gitleaks-report.json)

✅ Why it matters for you

In your DevOps projects (like ISD-App), adding Gitleaks ensures:

No secrets are pushed to GitHub accidentally

Keeps your pipelines secure (DevSecOps best practice)

Helps maintain compliance for production-ready code

4. linting - refers to the automated process of analyzing your code for potential errors, stylistic inconsistencies, and suspicious constructs. It's a form of static code analysis that helps improve code quality, maintainability, and consistency.

 . Static Code Analysis : For this i will divide it into two which is Software Composition Analysis (SCA) and Static Application Security Testing (SAST)
   
   . SAST: This checks the source code for coding error, will be using Sonarqube and Semgrep

5. Checkov can be integrated into GitHub Actions workflows to perform static analysis on Infrastructure as Code (IaC), container images, open source packages, and CI/CD configurations. This integration enables automated security and compliance checks as part of your CI/CD pipeline.

6. SCA (Software Composition Analysis): This helps to scan dependencies (e.g., Python, Node.js, Java, etc.) for vulnerabilities, Docker images for security issues and Infrastructure as Code (IaC) files (Terraform, Kubernetes, CloudFormation)

7. SBOM (Software Bill Of Material): Is like a "bill of ingredients" for your software.
It lists all the components, dependencies, and libraries (open-source and proprietary) used in your app — including their versions and licenses.

Why it’s important:

Helps you track vulnerabilities in dependencies.

Ensures license compliance.

Improves supply chain security (you know what’s inside your software).

Required for DevSecOps compliance frameworks like NIST, FedRAMP

The reason behins this is because a lot of the vulnerabilties that are found in Software which comes from the thirdparty libraries that the software is using.

The example of SBOM i used is called Syft

8. Image Scanner: Used Trivy for the Image Scanner. Trivy (by Aqua Security) is an open-source tool that scans for: OS package vulnerabilities (Ubuntu, Alpine, etc.), Application dependencies (npm, pip, etc.), Docker image vulnerabilities, IaC misconfigurations (Terraform, Kubernetes YAML, etc.), Secrets in source code, SBOMs (Software Bill of Materials). It’s basically a Swiss Army knife for DevSecOps scanning.

9. DAST - Dynamic Application Security Testing (DAST) into GitHub Actions involves using a DAST tool to scan a running application and incorporating the results into your CI/CD pipeline. This enables automated security testing during development, identifying vulnerabilities that only manifest at runtime. We will be using OWASP ZAP: The zaproxy/action-full-scan action runs a full ZAP scan and can report results as GitHub issues.