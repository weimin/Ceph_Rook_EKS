# Ceph_Rook_EKS

A repository for installing Ceph and Rook on EKS

Instructions to setup the Cluster:

1. run cd ClusterSetup/EKS
2. run terraform init
3. run terraform apply, it should list about 52 items and enter yes
4. There will be some errors but thats alright. run ls to list all files, you should see a file like "kubeconfig_test-eks-XXXXXXX" where XXXXXXX is a random string
5. We need to export our kubeconfig e.g. export KUBECONFIG=kubeconfig_test-eks-HeuUo1Vp and run terraform apply again.
6. run terraform apply you should see a green blob of text if everything went well. EKS cluster is now up
7. Execute kubectl create -f ~/Ceph_Rook_EKS/ClusterSetup/rook_ceph/common.yaml then create -f ~/Ceph_Rook_EKS/ClusterSetup/rook_ceph/operator.yaml then kubectl create -f ~/Ceph_Rook_EKS/ClusterSetup/rook_ceph/cluster-on-pvc.yaml 
8. Now ceph rook should be installed
9. Follow [https://zero-to-jupyterhub.readthedocs.io/en/latest/setup-jupyterhub/setup-jupyterhub.html](https://zero-to-jupyterhub.readthedocs.io/en/latest/setup-jupyterhub/setup-jupyterhub.html) to setup helm then add jupyterHUB to the cluster

Instructions to view the Ceph Dashboard:
1. Run kubectl create -f ~/Ceph_Rook_EKS/ClusterSetup/rook_ceph/dashboard-ingress-https.yaml
2. Register a domain name on namecheap
3. On the aws console under Load Balancers there should be an A-record address. Add a cname record and use that address as the target for the domain name that was registered. Then if your domain name was http://www.abc.com open the address with your browser.
4. Get login credentials for the Ceph dashboard by following the instructions here: https://rook.io/docs/rook/v1.3/ceph-dashboard.html 

