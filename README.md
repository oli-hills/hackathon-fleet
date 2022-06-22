# hackathon-fleet

```
flux bootstrap github \
  --owner=$GITHUB_USER \
  --repository=hackathon-fleet \
  --branch=main \
  --path=./clusters/cluster-flux \
  --personal
  ```

  ```
  flux create source git hackathon-app \
  --url=https://github.com/oli-hills/hackathon-app \
  --branch=master \
  --interval=30s \
  --export > ./clusters/cluster-flux/hackathon-app.yaml
  ```

  ```
  flux create kustomization podinfo \
  --target-namespace=podinfo \
  --source=podinfo \
  --path="./kustomize" \
  --prune=true \
  --interval=5m \
  --export > ./clusters/cluster-flux/Apps/podinfo/podinfo-kustomization.yaml
  ```

  ```
  flux create source git podinfo \
  --url=https://github.com/stefanprodan/podinfo \
  --branch=master \
  --interval=30s \
  --export > ./base/namespaces/info/podinfo/repo.yaml
  ```

  ```
  flux create kustomization podinfo \
  --target-namespace=info \
  --source=podinfo \
  --path="./kustomize" \
  --prune=true \
  --interval=5m \
  --export > ../base/namespaces/info/podinfo/kustomization.yaml
  ```