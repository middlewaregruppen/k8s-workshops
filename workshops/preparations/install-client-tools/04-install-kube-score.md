Install kube-score
---
🏠 [Home](/workshops/preparations/README.md) ∙ [Go Back](/workshops/preparations/02-install-client-tools.md)

`kube-score` is a tool that performs static code analysis of your Kubernetes object definitions. The output is a list of recommendations of what you can improve to make your application more secure and resilient.

## Linux
```
curl -Lo kube-score https://github.com/zegl/kube-score/releases/download/v1.14.0/kube-score_1.14.0_linux_amd64
```

## macOS (intel)
```
curl -Lo kube-score https://github.com/zegl/kube-score/releases/download/v1.14.0/kube-score_1.14.0_darwin_amd64
```

## macOS (Apple Silicon)
```
curl -Lo kube-score https://github.com/zegl/kube-score/releases/download/v1.14.0/kube-score_1.14.0_darwin_arm64
```

## Windows 
```
curl -Lo kube-score.exe https://github.com/zegl/kube-score/releases/download/v1.14.0/kube-score_1.14.0_windows_amd64.exe
```

## Verify
```
kube-score version
```