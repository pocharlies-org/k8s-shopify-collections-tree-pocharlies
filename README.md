# k8s-shopify-collections-tree-pocharlies

GitOps manifests for the Skirmshop Collections Tree Shopify app.

This app serves `https://skirmshop.e-dani.com/collections-tree` and replaces the
legacy Sauvage localhost route on port `3473`.

## Runtime

- Namespace: `skirmshop`
- Service: `collections-tree-app`
- Public path: `skirmshop.e-dani.com/collections-tree`
- Database: `collections_tree` on `postgres-shared-rw.databases.svc.cluster.local`
- Brain: `skirmshop-brain.skirmshop-brain-prod.svc.cluster.local`
- Shopify events: `shared-rabbitmq.databases.svc.cluster.local`, vhost `/synapse`

## Secrets

`collections-tree-secrets` is currently a manual Kubernetes Secret copied from
the legacy Sauvage env files because the current Vault Kubernetes role cannot
write `secret/skirmshop/collections-tree`.

Move this Secret to Vault/ExternalSecret before deleting the legacy env files.
