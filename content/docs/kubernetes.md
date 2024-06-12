# Kubernetes

For real production. Docker swarm might not be enough. If something load balanced and scalable is needed, kubernetes is a well-known solution.

This is why we made kubernetes deployments for this application, that create every pods needed to run Uni-Verse flawlessly, pulling it from our CI/CD generated docker registry images.

Here are the different kubernetes config files available for the production:

| Service                                                                             |                               Files |
| :---------------------------------------------------------------------------------- | ----------------------------------: |
| [Api](https://github.com/uni-verse-fm/uni-verse-api/tree/main/kubernetes/api)       | Configmap, Deployment, Service, PVC |
| [MongoDB](https://github.com/uni-verse-fm/uni-verse-api/tree/main/kubernetes/api)   |            Deployment, PVC, Service |
| RabbitMQ                                                                            |                          Helm Chart |
| [FP workers](https://github.com/uni-verse-fm/uni-verse-worker)                      |            PVC, Service, Deployment |
| Elastic search                                                                      |                          Helm Chart |
| FileBeat                                                                            |                           Daemonset |
| Kibana                                                                              |                          Helm Chart |
| MinIO                                                                               |                          Helm Chart |
| (Frontend)[https://github.com/uni-verse-fm/uni-verse-frontend/tree/main/kubernetes] |                 Deployment, Service |
