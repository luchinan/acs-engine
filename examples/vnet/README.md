# Microsoft Azure Container Service Engine - Custom VNET

## Overview

These examples show you how to build a customized Docker enabled cluster on Microsoft Azure where you can provide your own VNET.

To try: 

1. first deploy a custom vnet.  An example of an arm template that does this is under directory vnetarmtemplate.
2. next configure the example templates and deploy according to the examples:
 1. **dcos.json** - deploying and using [DC/OS](../../docs/dcos.md)
 2. **kubernetes.json** - deploying and using [Kubernetes](../../docs/kubernetes.md).  To try out the example configuration here, run these steps from this directory with a client which has `az` configured:
   a. Modify the export values and then execute the pre-deploy script:

   ```bash
   export SUBSCRIPTION=yoursubscriptionnumber
   export CLUSTER_DEFINITION=kubernetesvnet.json
   export LOCATION=westus
   export RESOURCE_GROUP=acsk8svnet
   ./k8s-vnet-predeploy.sh
   ```

   Ensure that the template has updated the `vnetSubnetId` value in the `kubernetesvnet.json` template to the value of the `id` output from the previous script and has added `/subnets/KubernetesSubnet` to the end.
   b. Generate the acs-engine template
   c. Deploy the generated template
   d. Run the `k8s-vnet-postdeploy.sh` script.
     > Note: If the vnet is in a different resource group than the K8s cluster, then update the script accordingly otherwise it will fail.

 3. **swarm.json** - deploying and using [Swarm](../../docs/swarm.md)
 4. **swarmmodevnet.json** - deploying and using [Swarm Mode](../../docs/swarmmode.md)

