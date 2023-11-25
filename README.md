# k8s-light-way
easy way to deploy production ready k8s cluster for training purpose
# how-to
* install `Vagrant`
* execute `vagrant up` command from project root folder
# deployment units
this IaC setup keeps your host absolutely clean, all components for k8s deployment are installed on `ansible-controller-node`

**demo set of deployment unuts:**
* k8s-master-node-1
* k8s-master-node-2
* k8s-worker-node-1
* k8s-worker-node-2
* ansible-controller-node

# vagrant file vars
* `VM_BOX = "debian/bookworm64"`
* `VM_BOX_VERSION = "12.20231009.1"`
* `KUBESPRAY_TAG = "v2.23.1"`
* `CONTROLLER_CPU = 1`
* `CONTROLLER_RAM = 1024`
* `MASTER_CPU = 2`
* `MASTER_RAM = 2048`
* `WORKER_CPU = 4`
* `WORKER_RAM = 4096`
* `CONTROLLER_IP = "192.168.56.10"`
* `MASTER_IP_ARRAY = ["192.168.56.11", "192.168.56.12"]`
* `WORKER_IP_ARRAY = ["192.168.56.13", "192.168.56.14"]`

***warn:*** if you want to increase qty of worker nodes, just add more IPv4 addresses in `WORKER_IP_ARRAY` but also change `declare -a IPS=(#{MASTER_IP_ARRAY[0]} #{MASTER_IP_ARRAY[1]} #{WORKER_IP_ARRAY[0]} #{WORKER_IP_ARRAY[1]} #{WORKER_IP_ARRAY[2]} ...)` command in `# ansible controller node deploy` section of `Vagrant` file and add new IPv4 there to
