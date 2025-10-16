# RDM Dashboard

Quick RDM dashboard deployment with Kustomize configuration for ArgoCD GitOps workflow.

## Config

The configuration deploys the RDM dashboard to the `invenio` namespace using Kustomize. This includes deployment, service, and ingress resources for external access via nginx ingress controller.

**TODO**: Currently using `invenio` namespace and `invenio-project` for testing purposes only. This should be changed to dedicated RDM namespace and project in production.

The application is configured to use the `ghcr.io/tugraz-rdm/rdm:devel` image (development branch) and will be accessible at `rdm.k3s.cyverse.at`.

## Usage

### ArgoCD UI Setup

1. Open ArgoCD UI and create a new application
2. Use these settings:
   - **Application Name**: `rdm-dashboard`
   - **Project**: `invenio-project`
   - **Repository URL**: `https://github.com/tugraz-rdm/argocd-deployments`
   - **Path**: `kustomize/rdm`
   - **Target Revision**: `argocd-rdm-deployment`
   - **Destination Namespace**: `invenio`
   - **Sync Policy**: Automated

## Configuration Details

- **Namespace**: `invenio` (for testing purposes)
- **Project**: `invenio-project`
- **Image**: `ghcr.io/tugraz-rdm/rdm:devel`
- **Port**: `3000`
- **Host**: `rdm.k3s.cyverse.at`
- **Ingress Class**: `nginx`

## Testing

The application will be automatically synced by ArgoCD and accessible at `http://rdm.k3s.cyverse.at/` once deployed.

More details: https://github.com/tugraz-rdm/argocd-deployments
