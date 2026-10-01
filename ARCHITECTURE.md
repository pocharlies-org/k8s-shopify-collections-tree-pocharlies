# ARCHITECTURE — k8s-shopify-collections-tree-pocharlies

Manifests de `shopify-collections-tree-app`. Código en `pocharlies-org/shopify-collections-tree-app`.

## Clientes y versiones
- Un Deployment web (puerto 3473, `skirmshop.e-dani.com/collections-tree`, ns `skirmshop`). Tronco: `main` (Application `shopify-collections-tree`, path `k8s`).

## Dependencias (ambos sentidos)
- Base `pocharlies/k8s-shopify-framework-pocharlies//base?ref=deploy/prod`; imagen `harbor.lan.e-dani.com/homelab/shopify-collections-tree-app`; Postgres compartido.

## Stack
Kustomize con base remota; sin Helm.

## Componentes compartidos
Base del framework y `scripts/verify-scopes.sh` + `k8s/expected-scopes.txt` (comprueba que los `SCOPES` desplegados coinciden con lo esperado).

## Cómo se construye
`k8s/kustomization.yaml` con parches inline (puerto, URL, scopes, `match`).

## Tests y validaciones
`reusable-ci.yml` y `scripts/verify-scopes.sh`.

## CI/CD y despliegue
`ci.yml`, `release.yml`. ArgoCD lee `main`.

## Decisiones y trampas
- Cambiar `SCOPES` obliga a actualizar `expected-scopes.txt` y a re-autorizar la app en Shopify.
