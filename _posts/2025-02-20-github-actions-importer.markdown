---
layout: post
title:  "Github Actions Importer"
date:   2025-02-20 16:55:42 +0000
categories: automation
---
Github have been the champions of source control and the development corner for many decades. Indeed, this industry reputation proved an attractive prospect for Microsoft, who, back in 2019, completed an [acquisition of Github][mgh] for a massive $7.5 billion. Since that time, as [techcrunch points out][tc], this relationship has been fruitful, producing Actions and Codespaces to name but two, without Github losing any of its own identity in the process; a remarkable example of two brand giants co-existing and co-creating impactful industry tooling. 

So what does this trajectory mean for organisations invested in Microsoft development tooling? For example, with many Azure DevOps features now available in Github (and arguably done better), do organisations need to be investing in Github tooling, migration efforts and workplace training to meet this development? There is not an immedidate need to ditch DevOps just yet, with many Github-powered features predominantely in the [Azure Devop's product roadmap][rm], however it would be wise to migrate parts of the developnent lifecycle to Github for organisational future proofing. With regards training developers in all things Github, there are [excellent resources provided by Microsoft][mf], and even certifications to prove your skill; I've taken and [passed the Github Foundations exam][gfc], and found it to be both comprehensive and timely. This blog will get you going on your migrations efforts, so stay locked in!

## Actions in action
One part of the development lifecycle done exceedingly well in Github is automated deployment (and security for that matter, but that's for another blog post). Github Actions are a powerful and natural evolution of Azure DevOps pipelines, staples of Continuous Integration / Continuous delivery (CI/CD) in Microsoft territory. For those organisations invested heavily in DevOps pipelines but wish to utilise these Github capabilities, Github have produced an astonishingly powerful migration tool that will analyse your existing DevOps project, replicate your YML pipeline definitions into your Github repository, and with graceful handling of DevOps pipeline nomenclature, get DevOps (surely now "GitOps") engineers working deployment automation workflows almost instantly. Very impressive stuff, and who doesn't like almost painless migration! Spinning up a Github Codespace within your target repository, you can perform the following steps:

## Install the Github Actions Importer

When the Codespace finishes spinning up, you will be presented with a bash shell; incidently, the look and feel of the Codespace will be familiar to those developers used to working in Microsoft Visual Studio Code (Microsoft code-reuse in action!). Enter the following command in your shell prompt to install the Github Actions importer:

```bash
gh extension install github/gh-actions-importer
```
## Verify the version

You can verify the install went successfully by running:

```bash
gh actions-importer version
```
## Establishing DevOps-Github connectivity and verifying the environment
Once the importer has been installed within your Codespace, follow steps 1-3 within the [Github configuring credentials guide][ghcc] to configure the credentials for connectivity between Azure DevOps and Github. If the connectivity is established successfully, an environment file (<code>.env.local</code>) will be created within your repository route that contains the various tokens and URLs needed to perform the audit, handy for performing future audits should you need to. <b>Important:</b> For security reasons, it's imperative NOT to store these environment variables within public repository source control! The DevOps PAT, which should be created with the shortest possible lifespan, used as one half of the connectivity agreement has the following scopes, which are extensive privileges in the wrong hands:

- Agents Pool: <code>Read</code>
- Build: <code>Read & execute</code>
- Code: <code>Read & write</code>
- Project and Team: <code>Read, write, & manage</code>
- Release: <code>Read</code>
- Service Connections: <code>Read</code>
- Task Groups: <code>Read</code>
- Variable Groups: <code>Read</code>

Finally, the environment can be verified using the following command:

```bash
gh actions-importer update
```
With connectivity established, we are now ready to perform an audit.

## Performing an audit
The <code>audit</code> command is used to connect to the DevOps organisation project from the Github Codespace, and convert each DevOps pipeline to their respective Github Actions workflow. The audit function is particulary powerful as it will simply comment-out parts of the pipeline definition YML file that it can't find exact transformations for, leaving you with workable workflows straight off the bat that can be tweaked to your liking. Running the following command will perform the audit, using the stored environment variables to establish connectivity, and outputing the audit reports to the output directory specified, in this instance, <code>tmp/audit</code>. It will also create workflow translations of your DevOps pipelines, writing the respective YML workflow definition files to the <code>pipelines/{project}</code> folder within the audit output directory.

```bash
gh actions-importer audit azure-devops --output-dir tmp/audit
```
The command output should resemble the following:

![audit command output][acimg]

[acimg]: /images/actions-importer/audit-command.png "Audit command output"

## The audit report
The audit report is created in markdown format, and contains a detailed breakdown of the DevOps pipeline definitions that it was able to convert, or did not find direct translations for. Instances where the importer could not perform direct translations are handled gracefully, and those specific sections within the YML workflows are commented out; refer to the [Github audit report summary page][ghars] for more details.

[ghcc]: https://github.com/actions/importer-labs/blob/main/azure_devops/1-configure.md#configuring-credentials
[ghars]: https://github.com/actions/importer-labs/blob/main/azure_devops/2-audit.md#review-audit-summary
[mgh]: https://blogs.microsoft.com/blog/2018/10/26/microsoft-completes-github-acquisition/
[tc]: https://techcrunch.com/2022/10/26/four-years-after-being-acquired-by-microsoft-github-keeps-doing-its-thing/
[rm]: https://learn.microsoft.com/en-us/azure/devops/release-notes/features-timeline
[mf]: https://examregistration.github.com/certification/GHF
[gfc]: https://www.credly.com/badges/f541d2b6-e348-41f5-bdd8-a5984a80c235/linked_in_profile
