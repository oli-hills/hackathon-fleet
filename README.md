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