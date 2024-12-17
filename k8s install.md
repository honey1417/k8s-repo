## k8s installation ( BOTH MASTER AND WORKER )
```bash
# First, install necessary packages for apt repository management:
#https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/
sudo apt-get install -y apt-transport-https ca-certificates curl gpg
```
```bash
# If the directory `/etc/apt/keyrings` does not exist, it should be created before the curl command, read the note below.
sudo mkdir -p -m 755 /etc/apt/keyrings
```
```bash
# Add the Kubernetes repository key to securely authenticate packages:
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.32/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
```
```bash
# Add the Kubernetes repository to your system's list of package sources:
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.32/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
```
```bash
# Update the package lists to fetch information about the latest versions of packages available:
sudo apt-get update
```
```bash
# Install Kubernetes components including kubelet, kubeadm, and kubectl:
sudo apt-get install -y kubelet kubeadm kubectl
```
```bash
# To prevent accidental upgrades of Kubernetes packages, hold them at their current version:
sudo apt-mark hold kubelet kubeadm kubectl
```
