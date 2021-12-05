root@istio-k8s-01:~# history 
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
   21  br_netfilter
   22  EOF
   23  cat /etc/modules-load.d/k8s.conf 
   24  cat <<EOF | sudo tee /etc/sysctl.d/k8s.conf
   25  net.bridge.bridge-nf-call-ip6tables = 1
   26  net.bridge.bridge-nf-call-iptables = 1
   27  EOF
   28  cat /etc/sysctl.d/k8s.conf 
   29  sudo sysctl --system
   30  sudo apt-get update
   31  sudo apt-get install -y apt-transport-https ca-certificates curl
   32  sudo curl -fsSLo /usr/share/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg
   33  echo "deb [signed-by=/usr/share/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
   34  sudo apt-get update
   35  sudo apt-get install -y kubelet kubeadm kubectl
   36  sudo apt-mark hold kubelet kubeadm kubectl
   37  sudo kubeadm init
   38  mkdir -p $HOME/.kube
   39  sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
   40  sudo chown $(id -u):$(id -g) $HOME/.kube/config
   41  kubectl get nodes
   42  kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
   43  kubectl get nodes
   44  kubectl get pod -n kube-system -w
   45  kubectl get nodes -o wide
   46  history 
   47  kubectl get nodes -o wide
   48  source <(kubectl completion bash)
   49  kubectl get nodes
   50  kubectl get pods
   51  kubectl get pod
   52  curl -L https://istio.io/downloadIstio | sh -
   53  ls
   54  export PATH="$PATH:/root/istio-1.11.4/bin"
   55  hostname
   56  cd istio-1.11.4/
   57  istioctl install --set profile=demo -y
   58  kubectl label namespace default istio-injection=enabled
   59  kubectl get namespaces 
   60  kubectl get namespaces default -o yaml
   61  ls
   62  kubectl apply -f samples/bookinfo/platform/kube/bookinfo.yaml
   63  vim samples/bookinfo/platform/kube/bookinfo.yaml
   64  kubectl get pods -n istio-system
   65  kubectl get services
   66  kubectl get pods
   67  kubectl exec "$(kubectl get pod -l app=ratings -o jsonpath='{.items[0].metadata.name}')" -c ratings -- curl -sS productpage:9080/productpage | grep -o "<title>.*</title>"
   68  kubectl get pods -n istio-system
   69  kubectl get namespaces --all-namespaces
   70  kubectl get pods -n default 
   71  kubectl describe pods details-v1-79f774bdb9-pltkl
   72  kubectl get services -n istio-system 
   73  kubectl apply -f samples/bookinfo/networking/bookinfo-gateway.yaml
   74  vim samples/bookinfo/networking/bookinfo-gateway.yaml
   75  kubectl get gateways.networking.istio.io 
   76  kubectl get gateway
   77  kubectl describe gateways.networking.istio.io 
   78  kubectl get svc istio-ingressgateway -n istio-system
   79  kubectl get svc -n istio-system 
   80  kubectl apply -f samples/addons
   81  kubectl rollout status deployment/kiali -n istio-system
   82  kubectl get svc -n istio-system 
   83  kubectl get svc -n istio-system | grep kiali
   84  kubectl port-forward svc/kiali 20001:20001 -n istio-system --address 0.0.0.0
   85  history 
   86  poweroff 
   87  kubectl get nodes
   88  kubectl get pods
   89  kubectl get gateways
   90  kubectl get svc istio-ingressgateway -n istio-system
   91  kubectl get svc
   92  source <(kubectl completion bash)
   93  kubectl get svc gateways.networking.istio.io
   94  kubectl get svc istio-ingressgateway -n istio-system
   95  ll
   96  cd istio-1.11.4
   97  ll
   98  vim samples/bookinfo/networking/bookinfo-gateway.yaml
   99  kubectl get gateways.networking.istio.io
  100  kubectl get gateway
  101  kubectl get svc -n istio-system | grep kiali
  102  kubectl get virtualservices.networking.istio.io
  103  kubectl get virtualservices.networking.istio.io bookinfo 