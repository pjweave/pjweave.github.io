---
layout: post
title:  "Github Actions Importer"
date:   2025-02-19 10:45:42 +0000
categories: automation
---
<p>First draft</p>

<h2>Install the Github Actions Importer</h2>

```bash
gh extension install github/gh-actions-importer
```
</p>
<h2>Verify the version</h2>

```bash
gh actions-importer version
```
<h2>Establishing DevOps-Github connectivity and verifying the environment</h2>
<p>Once the importer has been installed within Codespaces, follow steps 1-3 within the [Github configuring credentials guide][ghcc] to configure the credentials for connectivity between Azure DevOps and Github. If the connectivity is established, an environment file will be created within your repository that contains the various tokens and URLs, handy for performing future audits should you need to. It's import NOT to store these environment variables within public repository source control and it can be viewed by the world and would pose a massive security risk! Finally, the environment can then be verified using the following command.</p>

```bash
gh actions-importer update
```
<p>With connectivity established, we are now ready to perform an audit.</p>

<h2>Performing an audit</h2>
<p>The audit command is used to connect to the DevOps organisation project from Github, and convert each DevOps pipeline to their respective Github Actions workflow. The audit function is particulary powerful as it will simply comment-out parts of the pipeline definition YML file that it can't find exact transformations for, leaving you with workable workflows straight off the bat that can be tweaked to your liking. Running the following command will perform the audit, using the stored environment variables to establish connectivity, and outputing the audit reports to the output directory specified, in this instance, <code>tmp/audit</code>. It will also create workflow translations of your DevOps pipelines, writing the respective YML workflow definition files to the <code>pipelines/{project}</code> folder within the audit output directory.</p>

```bash
gh actions-importer audit azure-devops --output-dir tmp/audit
```
<h2>The audit report</h2>
<p>The audit report is created in markdown format, and contains a detailed breakdown of the DevOps pipeline definitions that it was able to convert, or did not find direct translations for. Instances where the importer could not perform direct translations are handled gracefully, and those specific sections within the YML workflows are commented out; refer to the [Github audit report summary page][ghars] for more details.</p>

[ghcc]: https://github.com/actions/importer-labs/blob/main/azure_devops/1-configure.md#configuring-credentials
[ghars]: https://github.com/actions/importer-labs/blob/main/azure_devops/2-audit.md#review-audit-summary
