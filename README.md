# Istio
Instalação do Istio em um Cluster Kubernetes na Digital Ocean para acompanhamento do curso Descomkplicando Istio da LinuxTips
Video de referencia: https://www.youtube.com/watch?v=DXw6NODrIpc

    1  sudo apt-get update
    2  swapoff -a
    3  sudo modprobe overlay 
    4  sudo modprobe br_netfilter 
    5  vi /etc/modules-load.d/containerd.conf
    6  vi etc/sysctl.d/99-kubernetes-cri.conf
    7  vi /etc/sysctl.d/99-kubernetes-cri.conf
    8  cat /etc/sysctl.d/99-kubernetes-cri.conf
    9  sudo sysctl --system
   10  sudo apt-get install containerd -y
   11  containerd config default
   12  sudo mkdir -p /etc/containerd
   13  containerd config default
   14  containerd config default | sudo tee /etc/containerd/config.toml
   15  cat  /etc/containerd/config.toml
   16  sudo systemctl restart containerd
   17  lsmod | grep br_netfilter
   18  cat /etc/modules-load.d/k8s.conf
   19  containerd
   20  cat <<EOF | sudo tee /etc/modules-load.d/k8s.conf
   br_netfilter
   EOF

   21  cat /etc/modules-load.d/k8s.conf 
   22  cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf
   net.bridge.bridge-nf-call-ip6tables = 1
   net.bridge.bridge-nf-call-iptables = 1
   EOF

   23  cat /etc/sysctl.d/k8s.conf 
   24  sudo sysctl --system
   25  sudo apt-get update
   26  sudo apt-get install -y apt-transport-https ca-certificates curl
   27  sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
   28  echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
   29  sudo apt-get update
   30  sudo apt-get install -y kubelet kubeadm kubectl
   31  sudo apt-mark hold kubelet kubeadm kubectl
   32  sudo kubeadm init
   33  mkdir -p $HOME/.kube
   34  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
   35  sudo chown $(id -u):$(id -g) $HOME/.kube/config
   36  kubectl get nodes
   37  kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
   38  kubectl get nodes
   39  kubectl get pod -n kube-system -w
   40  kubectl get nodes -o wide
   41  history 
   42  kubectl get nodes -o wide
   43  source <(kubectl completion bash)
   44  kubectl get nodes
   45  kubectl get pods
   46  kubectl get pod
   47  curl -L https://istio.io/downloadIstio | sh -
   48  ls
   49  export PATH="$PATH:/root/istio-1.11.4/bin"
   50  hostname
   51  cd istio-1.11.4/
   52  istioctl install --set profile=demo -y
   53  kubectl label namespace default istio-injection=enabled
   54  kubectl get namespaces 
   55  kubectl get namespaces default -o yaml
   56  ls
   57  kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml
   58  vim samples/bookinfo/platform/kube/bookinfo.yaml
   59  kubectl get pods -n istio-system
   60  kubectl get services
   61  kubectl get pods
   62  kubectl exec "$(kubectl get pod -l app=ratings -o jsonpath='{.items[0].metadata.name}')" -c ratings -- curl -sS productpage:9080/productpage | grep -o "<title>.*</title>"
   63  kubectl get pods -n istio-system
   64  kubectl get namespaces --all-namespaces
   65  kubectl get pods -n default 
   66  kubectl describe pods details-v1-79f774bdb9-pltkl
   67  kubectl get services -n istio-system 
   68  kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml
   69  vim samples/bookinfo/networking/bookinfo-gateway.yaml
   70  kubectl get gateways.networking.istio.io 
   71  kubectl get gateway
   72  kubectl describe gateways.networking.istio.io 
   73  kubectl get svc istio-ingressgateway -n istio-system
   74  kubectl get svc -n istio-system 
   75  kubectl apply -f samples/addons
   76  kubectl rollout status deployment/kiali -n istio-system
   77  kubectl get svc -n istio-system 
   78  kubectl get svc -n istio-system | grep kiali
   79  kubectl port-forward svc/kiali 20001:20001 -n istio-system --address 0.0.0.0
