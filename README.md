# Overview
Homelab-argocd project is generally to be used for automatic management of current HomeLab installation via ArgoCD.

Main approach for this project is creating stable, as-automatic-as-possible deployment of Homelab to kubernetes cluster, 
that should properly backup to on-site and off-site storage with support for easy recovery.

# Installation
## Prerequisites
This project assumes already installed ArgoCD application in argocd namespace.

Also, each application technically refers to this same repository, so in case of using other repository/fork/local git
installation, reference should be updated (can be found by 'repoURL: ' anchor)

## Installation
- Install ArgoCD. It is recommended to use official ArgoCD repository (reference and values.yaml used by me can be found
in this repository, in folder 'backend')
- Create project and configure destination to match target used cluster and source to list all required repositories
- Apply [app-in-app config](homelab.yaml) file to argocd namespace. This should create argocd Application,
that will recursively pull all other applications
- This will also install SealedSecrets instance. For backing up and restoring, please refer to official documentation.
