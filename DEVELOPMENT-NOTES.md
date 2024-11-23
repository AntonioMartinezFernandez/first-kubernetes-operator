# first-kubernetes-operator

K8s Operators practice with Kubebuilder

## Prerequisites

- [Go](https://go.dev/)
- [Orbstack](https://orbstack.dev/)
- [Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)
- [Openlens](https://formulae.brew.sh/cask/openlens)
- [Openlens Node Pod Menu Extension](https://medium.com/geekculture/fix-essential-functionality-missing-in-the-new-openlens-version-f9ac862e9e27)

## Resources

- [Kubebuilder Book](https://book.kubebuilder.io/quick-start.html)

## Install kubebuilder

```bash
curl -L -o kubebuilder "https://go.kubebuilder.io/dl/latest/$(go env GOOS)/$(go env GOARCH)"
chmod +x kubebuilder && sudo mv kubebuilder /usr/local/bin/
```

## Create a new project

```bash
mkdir first-kubernetes-operator
cd first-kubernetes-operator
kubebuilder init --domain mydomain.com --repo mydomain.com/first-kubernetes-operator
```
