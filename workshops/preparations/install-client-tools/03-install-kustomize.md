Install kustomize
---
🏠 [Home](/workshops/preparations/README.md) ∙ [Go Back](/workshops/preparations/02-install-client-tools.md)

`kustomize` introduces a template-free way to customize application configuration that simplifies the use of off-the-shelf applications. It is built into `kubectl` as `kubectl apply -k` but we are going to use it on its own.

## Binary install
The following script detects your OS and downloads the appropriate kustomize binary to your current working directory.
```
curl -s "https://raw.githubusercontent.com/kubernetes-sigs/kustomize/master/hack/install_kustomize.sh"  | bash
sudo mv ./kustomize /usr/local/bin/kustomize
```

## Verify
```
kustomize version
```