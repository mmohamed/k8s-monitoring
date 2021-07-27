# Kubernetes Monitoring App for Raspberry

[![CircleCI](https://circleci.com/gh/mmohamed/k8s-monitoring.svg?style=svg)](https://circleci.com/gh/mmohamed/k8s-monitoring)

Goal is to deploy a simple application for cluster resources monitoring. Target resources will be CPU charge, Memory consuming, CPU temperature and pods state like in Top view on Linux system.

##### [@See for full description](https://blog.medinvention.dev/k8s-cpu-temperature-fan-monitoring-for-rpi/)

----

<img src="https://blog.medinvention.dev/content/images/2020/04/FAN-CPU-Diagram-Full.jpg" width="900">


### Tips
- Build docker images for ARM32 and AMR64 with BuildX : 
```bash
# build images
docker buildx build -f Dockerfile.api --build-arg ARCH=arm32v7 --platform linux/arm/v7 --tag medinvention/k8s-monitoring-api:arm32v7-1.0.0 . --load
docker buildx build -f Dockerfile.api --build-arg ARCH=arm64v8 --platform linux/arm64/v8 --tag medinvention/k8s-monitoring-api:arm64v8-1.0.0 . --load
# push images
docker push medinvention/k8s-monitoring-api:arm32v7-1.0.0
docker push medinvention/k8s-monitoring-api:arm64v8-1.0.0
# create manifest
docker manifest create medinvention/k8s-monitoring-api:1.0.0 --amend medinvention/k8s-monitoring-api:arm32v7-1.0.0 --amend medinvention/k8s-monitoring-api:arm64v8-1.0.0
# push manifest
docker manifest push medinvention/k8s-monitoring-api:1.0.0 
```

---- 

[*More informations*](https://blog.medinvention.dev)
