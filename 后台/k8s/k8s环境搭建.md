### 配置docker加速器
 ```
mkdir -p /etc/docker tee /etc/docker/daemon.json <<-'EOF' { "registry-mirrors": ["https://fl791z1h.mirror.aliyuncs.com"] }EOF
systemctl daemon-reload systemctl restart docker
```
#添加阿⾥ kubernetes源
```
cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://mirrors.aliyun.com/kubernetes/yum/repos/kubernetes-el7-x86_64/
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://mirrors.aliyun.com/kubernetes/yum/doc/yum-key.gpg https://mirrors.aliyun. EOF
```
 #安装k8s相关组件
 ```
 yum install kubectl kubelet kubeadm systemctl enable kubelet
 ```


# 配置⽹络模式 cat > /etc/sysctl.d/k8s.conf << EOF net.bridge.bridge-nf-call-ip6tables = 1 net.bridge.bridge-nf-call-iptables = 1 EOF echo 1 > /proc/sys/net/bridge/bridge-nf-call-iptables echo 1 > /proc/sys/net/bridge/bridge-nf-call-ip6tables

##执⾏k8s初始化
```
kubeadm init \
 --apiserver-advertise-address=192.168.0.76 \
  --image-repository registry.aliyuncs.com/google_containers \
   --service-cidr=10.10.0.0/16
   --pod-network-cidr=10.122.0.0/16
```
## 访问192.168.0.76:6443网址
此时报错
```
{
"kind": "Status",
"apiVersion": "v1",
"metadata": {},
"status": "Failure",
"message": "forbidden: User \"system:anonymous\" cannot get path \"/\"",
"reason": "Forbidden",
"details": {},
"code": 403
}
```
执行后日志：
```
Your Kubernetes control-plane has initialized successfully!

To start using your cluster, you need to run the following as a regular user:

  mkdir -p $HOME/.kube
  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
  sudo chown $(id -u):$(id -g) $HOME/.kube/config

Alternatively, if you are the root user, you can run:

  export KUBECONFIG=/etc/kubernetes/admin.conf

You should now deploy a pod network to the cluster.
Run "kubectl apply -f [podnetwork].yaml" with one of the options listed at:
  https://kubernetes.io/docs/concepts/cluster-administration/addons/

Then you can join any number of worker nodes by running the following on each as root:

kubeadm join 192.168.0.76:6443 --token k518l7.qi85apfe9wmykmb6 \
    --discovery-token-ca-cert-hash sha256:d66259388d9bfe8339dad34b1fca95f5c889da5204a4b9ef695b49a376dde7cc
```
## join前先生成token和密钥
```
kubeadm token create --print-join-command
```
## 卸载k8s
```
kubeadm reset -f
modprobe -r ipip
lsmod
rm -rf ~/.kube/
rm -rf /etc/kubernetes/
rm -rf /etc/systemd/system/kubelet.service.d
rm -rf /etc/systemd/system/kubelet.service
rm -rf /usr/bin/kube*
rm -rf /etc/cni
rm -rf /opt/cni
rm -rf /var/lib/etcd
rm -rf /var/etcd
```
