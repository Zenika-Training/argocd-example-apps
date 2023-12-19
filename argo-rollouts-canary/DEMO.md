# Demo

- Edit the top level domain in canary-ingress.yaml and canary-preview-ingress.yaml
- Expose argo rollouts dashboard:
`kubectl port-forward -n argo-cd svc/argo-rollouts-dashboard 3100`
- Open dashboard in browser
- `kubectl apply -k .`
- Open `canary-demo.${TOP_LEVEL_DOMAIN}`
- Traffic is 100% green
- Edit image tag in ./canary-rollout.yaml from **green** to **blue**
- Traffic will switch automatically to 80% green / 20% blue
- The `pause: {}` in the rollout descriptor will make `argo-rollouts` wait for a manual approval
- Go to the dashboard and click the promote button
- Traffic will begin switching to 40% for 10s, then 60% for 10s ...
