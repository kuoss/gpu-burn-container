# gpu-burn-container

https://github.com/wilicc/gpu-burn


```
docker run --rm --gpus all ghcr.io/kuoss/gpu-burn
```

alerternatives:
- nvcr.io/nvidia/k8s/cuda-sample:nbody
- nvcr.io/nvidia/k8s/cuda-sample:nbody-cuda11.7.1
- nvcr.io/nvidia/k8s/cuda-sample:nbody-cuda11.7.1-ubuntu18.04
- nvcr.io/nvidia/k8s/cuda-sample:nbody-cuda11.6.0
- nvcr.io/nvidia/k8s/cuda-sample:nbody-cuda11.6.0-ubuntu18.04
- nvcr.io/nvidia/k8s/cuda-sample:nbody-cuda11.2.1
- nvcr.io/nvidia/k8s/cuda-sample:nbody-cuda11.1
 
https://catalog.ngc.nvidia.com/orgs/nvidia/teams/k8s/containers/cuda-sample/tags

```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: sample
spec:
  selector:
    matchLabels:
      app: sample
  template:
    metadata:
      labels:
        app: sample
    spec:
      containers:
      - name: sample
        image: nvcr.io/nvidia/k8s/cuda-sample:nbody-cuda11.2.1
        args: ["nbody", "-gpu", "-benchmark", "-numbodies=2560000"]
        resources:
          limits:
            nvidia.com/gpu: 1
```
