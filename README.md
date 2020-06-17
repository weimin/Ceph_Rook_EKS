# Ceph_Rook_EKS

A repository for installing Ceph and Rook on EKS

Instructions:

1. run cd ClusterSetup/EKS
2. run terraform init
3. run terraform apply, it should list about 52 items and enter yes
4. There will be some errors but thats alright. $ls to list all files you should see a file like "kubeconfig_test-eks-XXXXXXX" where XXXXX is a random string
5. so we need to export our kubeconfig, e.g. export KUBECONFIG=kubeconfig_test-eks-HeuUo1Vp
6. run terraform apply you should see a green blob of text if everything went well. EKS cluster is now up
7. Execute kubectl create -f /Users/weimin/Documents/Ceph_Rook_EKS/ClusterSetup/rook_ceph/common.yaml then create -f /Users/weimin/Documents/Ceph_Rook_EKS/ClusterSetup/rook_ceph/operator.yaml then kubectl create -f /Users/weimin/Documents/Ceph_Rook_EKS/ClusterSetup/rook_ceph/cluster-on-pvc.yaml 
8. Now ceph rook should be installed
9. Follow [https://zero-to-jupyterhub.readthedocs.io/en/latest/setup-jupyterhub/setup-jupyterhub.html](https://zero-to-jupyterhub.readthedocs.io/en/latest/setup-jupyterhub/setup-jupyterhub.html) to add jupyterHUB to the cluster
