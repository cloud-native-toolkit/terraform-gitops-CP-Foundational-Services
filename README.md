# Starter kit for the ibm-common-services Terraform GitOps module

This is a terraform module that will install Cloud Pak Foundational services (`ibm-common-services-operator`) subscription into an OpenShift cluster.
## Software dependencies

The module depends on the following software components:

### Command-line tools

- terraform - v12
- kubectl

### Terraform providers

- IBM Cloud provider >= 1.5.3
- Helm provider >= 1.1.1 (provided by Terraform)

## Module dependencies

This module makes use of the output from other modules:

- GitOps - github.com/cloud-native-toolkit/terraform-tools-gitops.git
- Namespace - github.com/cloud-native-toolkit/terraform-gitops-namespace.git
- etc

## Example usage

```hcl-terraform
module "gitops_module" {
  source = "https://github.com/cloud-native-toolkit/terraform-gitops-cp-foundational-services"

  gitops_config = module.gitops.gitops_config
  git_credentials = module.gitops.git_credentials
  server_name = module.gitops.server_name
  namespace = module.gitops_namespace.name
  kubeseal_cert = module.gitops.sealed_secrets_cert
}

```
