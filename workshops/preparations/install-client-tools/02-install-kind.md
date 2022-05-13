# Install kind
---
🏠 [Home](/workshops/preparations/README.md) ∙ [Go Back](/workshops/preparations/02-install-client-tools.md)

[kind](https://kind.sigs.k8s.io/) is a tool for running local Kubernetes clusters using Docker container “nodes”. kind was primarily designed for testing Kubernetes itself, but may be used for local development or CI. 

## If you have Go 1.17+ installed
```
go install sigs.k8s.io/kind@v0.12.0
sudo mv $GOPATH/bin/kind /usr/local/bin/kind
```

## Linux
```
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.12.0/kind-linux-amd64
chmod +x ./kind
mv ./kind /some-dir-in-your-PATH/kind
```

## macOS (intel)
```
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.12.0/kind-darwin-amd64
chmod +x ./kind
mv ./kind /some-dir-in-your-PATH/kind
```

## Windows in PowerShell
```
curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.12.0/kind-windows-amd64
Move-Item .\kind-windows-amd64.exe c:\some-dir-in-your-PATH\kind.exe
```
If you don't have `curl.exe` you can download kind [here](https://kind.sigs.k8s.io/dl/v0.12.0/kind-windows-amd64)

## Verify kind
```
kind version
```