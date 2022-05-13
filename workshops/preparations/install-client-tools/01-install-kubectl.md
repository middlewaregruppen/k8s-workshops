Install kubectl
---
🏠 [Home](/workshops/preparations/README.md) ∙ [Go Back](/workshops/preparations/02-install-client-tools.md)

`kubectl` is the main tool used to interact with any cluster. It's important that you install this one

## Linux
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/kubectl
```

## macOS Intel
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/kubectl
```

## macOS Apple Silicon
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/arm64/kubectl"
```

## Windows
[Download latest release v1.23.0 here](https://dl.k8s.io/release/v1.23.0/bin/windows/amd64/kubectl.exe).

**Note:** To find out the latest stable version (for example, for scripting), take a look at https://dl.k8s.io/release/stable.txt

Or if you have `curl` installed, use this command:
```
curl -LO "https://dl.k8s.io/release/v1.23.0/bin/windows/amd64/kubectl.exe"
```
Append or prepend the kubectl binary to your PATH environment variable.