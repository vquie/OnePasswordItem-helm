    This helm chart allows to set deployment independent secrets from 1Password. The main feature is, you can use it via helmfile.

## Example values
```
---
secrets:
  default:		     	# < this is the kubernetes namespace
    - item: "vaults/<vault_id_or_title>/items/<item_id_or_title>"
      name: "secret1"	# < name of the created kubernetes secret
      type: Opaque		# < type of the created kubernetes secret
    - item: "vaults/<vault_id_or_title>/items/<item_id_or_title>"
      name: "secret2"
      type: kubernetes.io/dockerconfigjson
  example-namespace:  	# < this is another kubernetes namespace
    - item: "vaults/<vault_id_or_title>/items/<item_id_or_title>"
      name: "secret3"
    - item: "vaults/<vault_id_or_title>/items/item_id_or_title>"
      name: "secret4"
```

## usage
```
# install repo
helm repo add vquie https://vquie.github.io/helm-charts
helm repo update

# install chart
helm upgrade --install --namespace your-namespace 1password-secrets-release vquie/onepassworditem -f values.yaml
```