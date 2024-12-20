# ghostfolio-k8s

[Ghostfolio](https://github.com/ghostfolio/ghostfolio/) is an open source wealth management software built with web technology. This project enables potential users to deploy the entire app on Kubernetes with [Helm](https://helm.sh/) 

## Why
With rising popularity of Kubernetes, this project will provide an alternative way to deploy the application on Kubernetes using Helm

## Dependencies

* `Kubernetes`
* `Helm`

## Deployment Guide 

Create new namespace

```bash
kubectl create namespace ghostfolio
```

Deploy Ghostfolio using Helm

```bash
helm upgrade --install ghostfolio . --namespace ghostfolio
```

Check if services are ready

```bash
kubectl get svc --namespace ghostfolio
```

Go to your browser and enter the following URL:

```
localhost:32333
```

### Using Secrets

In order to store sensitive data in Secrets this chart supports the loading of values from an existing Secret resource. In there the values for the following properties can be stored:

- PostgreSql connection-string
- JWT secret
- Ghostfilio Salt
- Redis Password

Create a `secret.yaml` with the base64 encoded values:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: ghostfolio-secret
type: Opaque
data:
  postgresqlConnectionString: cG9zdGdyZXNxbDovL3VzZXI6Z2hvc3Rmb2xpb0BnaG9zdGZvbGlvLXBvc3RncmVzcWwvcG9zdGdyZXM/Y29ubmVjdF90aW1lb3V0PTMwMCZzc2xtb2RlPXByZWZlcg==
  redisPassword: Z2hvc3Rmb2xpbw==
  jwtSecretKey: Z2hvc3Rmb2xpbw==
  accessTokenSalt: Z2hvc3Rmb2xpbw==
```

Deploy the secrets with `kubectl apply -f secret.yaml -n ghostfolio` and set the values in a `values.deployment.yaml` file:

```yaml
ghostfolio:
  existingSecret: ghostfolio-secret
  secretKeys:
    postgresqlConnectionString: postgresqlConnectionString
    redisPassword: redisPassword
    jwtSecretKey: jwtSecretKey
    accessTokenSalt: accessTokenSalt
```

It is possible to use this feature selectively. Leave the `ghostfolio.secretKeys.xxx` values empty to use the clear text values instead.

## Roadmap
- [x] Create Manifests file
- [x] Helm Integration Guide
- [x] Implement Secrets 

## Contributing

Pull requests are welcome. The premise of this script is to provide basic information, so keep that in mind. If you have a major feature idea, let's discuss it through the issues page first.

Of course, feel free to fork and create a more interactive experience!

## License

GPL v3
