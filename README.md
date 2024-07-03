*This action can only be run on Linux runners as it requires Docker to be available in the environment*

# Nats Action

Starts Nats server/cluster for automated CI/CD.


# Usage

```yaml
name: Test
on: [push]
jobs:
  test-cluster:
    runs-on: ubuntu-latest
    name: Test cluster

    steps:
      - name: Create Nats cluster
        uses: step-security/nats-action@v0
        with:
          port: "4222 4223 4224" # multiple different ports will start a cluster. single port will start a single server

      - name: test connection to cluster
        uses: onichandame/nats-client-action@master
        with:
          servers: "nats://localhost:4222 nats://localhost:4223 nats://localhost:4224"
          cluster: "true"
```
