# Setup

## Installation Pre-reads <a href="#pre-read" id="pre-read"></a>

* Know the basics of Kubernetes: [https://www.youtube.com/watch?v=PH-2FfFD2PU\&t=3s](https://www.youtube.com/watch?v=PH-2FfFD2PU\&t=3s).
* Know the [basics of kubectl](https://www.tutorialspoint.com/kubernetes/kubernetes\_kubectl\_commands.htm) commands.
* Know Kubernetes Kubernetes Resources via YAML, Deployments, Replica Sets, and Pods: [https://www.youtube.com/watch?v=ohSUtEfDefc](https://www.youtube.com/watch?v=ohSUtEfDefc).
* Know how to manage env values, secrets of any service deployed in Kubernetes: [https://www.youtube.com/watch?v=OW244LxB4oI](https://www.youtube.com/watch?v=OW244LxB4oI).
* Know how to port forward to a pod running inside k8s cluster and work locally [https://www.youtube.com/watch?v=TT3nd5n5Yus](https://www.youtube.com/watch?v=TT3nd5n5Yus).
* Know sops to secure your keys/credentials: [https://www.youtube.com/watch?v=DWzJ87KbwxA](https://www.youtube.com/watch?v=DWzJ87KbwxA).

## 1. Choose the Cloud <a href="#v-1-choose-the-cloud" id="v-1-choose-the-cloud"></a>

Choose your cloud and follow the instructions to set up a Kubernetes cluster before moving on to the deployment.

{% content-ref url="on-aws.md" %}
[on-aws.md](on-aws.md)
{% endcontent-ref %}

## 2. Deployment <a href="#2-deploy-digit" id="2-deploy-digit"></a>

{% embed url="https://core.digit.org/guides/installation-guide/quick-setup/2.-deployment" %}

## 3. Destroy the Cluster <a href="#5-destroy-the-cluster" id="5-destroy-the-cluster"></a>

Finally, clean up the cluster setup if you wish, using the following command. This will delete the entire cluster and other cloud resources that were provisioned for the DIGIT setup.

```
cd DIGIT-DevOps/infra-as-code/terraform/my-digit-eks
terraformdestroy​
```

## Conclusion <a href="#conclusion" id="conclusion"></a>

We have successfully created infra on cloud, and deployed DIGIT in the cluster.
