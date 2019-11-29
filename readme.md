# kubernetes二进制文件下载及镜像仓库下载

kubernetes v1.15.6的镜像

kubernetes二进制文件下载及镜像仓库下载；

kubernetes v1.15.6的镜像，在下载容器`docker pull quelle/kubenetes-download:v1.15.6`时，前面四个都在server里面包含了，只需要下载后面的pause,etcd,coredns，dashboard四个就可以了。

```bash
W1129 23:24:37.258507    4291 version.go:99] falling back to the local client version: v1.15.6
k8s.gcr.io/kube-apiserver:v1.15.6
k8s.gcr.io/kube-controller-manager:v1.15.6
k8s.gcr.io/kube-scheduler:v1.15.6
k8s.gcr.io/kube-proxy:v1.15.6
k8s.gcr.io/pause:3.1
k8s.gcr.io/etcd:3.3.10
k8s.gcr.io/coredns:1.3.1
```

后面四个利用docker pull 对应的镜像就可以下载，然后利用docker tag 命令打标签。

```bash
docker pull quelle/kubernetes-dashboard-amd64:v1.10.1
docker pull quelle/pause:3.1
docker pull quelle/k8setcd:3.3.10
docker pull quelle/coredns:1.3.1
docker pull quelle/projectcalico-org-cni:v3.3.1
docker pull quelle/cpvpa-amd64:v0.6.0
docker pull quelle/projectcalico-org-node:v3.3.1
docker pull quelle/nvidia-gpu-device-plugin:d18b678437fedc4ec4211c20b3e5469a137a44f989da43dc275e4f2678170db4
docker tag quelle/kubernetes-dashboard-amd64:v1.10.1 k8s.gcr.io/kubernetes-dashboard-amd64:v1.10.1
docker tag quelle/pause:3.1 k8s.gcr.io/pause:3.1
docker tag quelle/k8setcd:3.3.10 k8s.gcr.io/etcd:3.3.10
docker tag quelle/coredns:1.3.1 k8s.gcr.io/coredns:1.3.1
docker tag quelle/projectcalico-org-cni:v3.3.1  gcr.io/projectcalico-org/cni:v3.3.1
docker tag quelle/cpvpa-amd64:v0.6.0 k8s.gcr.io/cpvpa-amd64:v0.6.0
docker tag quelle/projectcalico-org-node:v3.3.1 gcr.io/projectcalico-org/node:v3.3.1
docker tag quelle/nvidia-gpu-device-plugin:d18b678437fedc4ec4211c20b3e5469a137a44f989da43dc275e4f2678170db4 k8s.gcr.io/nvidia-gpu-device-plugin@sha256:d18b678437fedc4ec4211c20b3e5469a137a44f989da43dc275e4f2678170db4

docker pull quelle/k8s-dns-kube-dns:1.14.13
docker pull quelle/k8s-dns-dnsmasq-nany:1.14.13
docker pull quelle/k8s-dns-sidecar:1.14.13

docker tag quelle/k8s-dns-kube-dns:1.14.13 k8s.gcr.io/k8s-dns-kube-dns:1.14.13
docker tag quelle/k8s-dns-dnsmasq-nany:1.14.13 k8s.gcr.io/k8s-dns-dnsmasq-nany:1.14.13
docker tag quelle/k8s-dns-sidecar:1.14.13 k8s.gcr.io/k8s-dns-sidecar:1.14.13

docker save k8s.gcr.io/k8s-dns-kube-dns:1.14.13 k8s.gcr.io/k8s-dns-dnsmasq-nany:1.14.13 k8s.gcr.io/k8s-dns-sidecar:1.14.13 > k8s-dns-1.14.13.tar

gcr.io/projectcalico-org/node:v3.3.1
gcr.io/projectcalico-org/cni:v3.3.1
k8s.gcr.io/cpvpa-amd64:v0.6.0
k8s.gcr.io/nvidia-gpu-device-plugin@sha256:d18b678437fedc4ec4211c20b3e5469a137a44f989da43dc275e4f2678170db4
```
