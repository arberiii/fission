# Sample Golang serverless function using Fission

## Quick start
For installing fission CLI using execute:
```bash
$ kubectl create namespace fission 
$ kubectl -n fission apply -f \
    https://github.com/fission/fission/releases/download/1.10.0/fission-all-1.10.0.yaml
$ curl -Lo fission https://github.com/fission/fission/releases/download/1.10.0/fission-cli-osx \
    && chmod +x fission && sudo mv fission /usr/local/bin/
```
Test that fission is installed:
```bash
$ fission version
```

Add the Go environment to your cluster:
```bash
$ fission environment create --name go --image fission/go-env-1.12:1.10.0 --builder fission/go-builder-1.12:1.10.0
```

Create golang env with builder image to build go plugin:
```bash
$ fission fn create --name helloworld --env go --src hw.go --entrypoint Handler
```

Deploy:
```bash
$ fission pkg info --name <pkg-name>
```

Test:
```bash
$ fission fn test --name helloworld
> Hello, world!
```
