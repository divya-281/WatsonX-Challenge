# Instana deployment options

Last Updated: 2024-06-28

Instana can be deployed either as a SaaS solution with the option of retaining data in the cloud, or as a self-hosted (on-premises) solution. With Instana, you have control of where your data resides, on the cloud or on-premises. Thus, Instana combines the simplicity of SaaS with the control of an on-premises deployment.

*   [Instana SaaS deployment](https://www.ibm.com/docs/en/instana-observability/current?topic=planning-deployment-options#instana-saas-deployment)
*   [Instana self-hosted deployment](https://www.ibm.com/docs/en/instana-observability/current?topic=planning-deployment-options#instana-self-hosted-deployment)
*   [Instana agent deployment](https://www.ibm.com/docs/en/instana-observability/current?topic=planning-deployment-options#instana-agent-deployment)

##  Instana SaaS deployment

If you want to deploy Instana SaaS, you need to install only Instana agents.

**Note:** Before you install Instana agents, you need to review the system requirements and outbound network access requirements, and prepare endpoints and keys.

*   [Instana agent requirements](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/agent_requirements.html)
*   [Instana sensor requirements](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/sensor_requirements.html)
*   [Outbound network access requirements: Instana SaaS deployments](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/saas_network_requirement.html)
*   [Preparing endpoints and keys](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/endpoints_and_keys.html)

1.  Install Instana agents as described in the [Instana agent deployment](https://www.ibm.com/docs/en/instana-observability/current?topic=planning-deployment-options#instana-agent-deployment) section.    
    
2.  Optional: The following features in Instana are disabled by default. To enable these features, [open a case with IBM Support](https://www.ibm.com/mysupport/s/). For more information about a feature, use the link that is provided in the list.

*   VMware Tanzu (PCF) feature: [Monitoring Cloud Foundry and VMware Tanzu (formerly know as Pivotal Cloud Foundry)](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/ecosystem/cloudfoundry/index.html)
*   VMware® vSphere feature: [Monitoring vSphere](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/ecosystem/vsphere/index.html)
*   IBM Z HMC feature: [Monitoring IBM Z HMC](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/ecosystem/zHMC/index.html)
*   IBM Power HMC feature: [Monitoring IBM Power HMC](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/ecosystem/pHMC/index.html)
*   IBM J9 VM memory leak detection feature: [The JVM section of the Built-in Events Reference page](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/events_alerts/built-in-events-ref.html#jvm)

3.  Administer your Instana Tenant, such as onboarding users, managing API, agent keys, and role-based access control (RBAC), configuring user interface settings, and viewing audit logs. For more information, see [Administer Instana](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/admin/index.html).

##  Instana self-hosted deployment

If you want to deploy Instana in your on-premises environment, you need to install both the Instana backend (Instana server) and Instana agents.

**Note:** Before you install Instana, you need to review the system requirements and outbound network access requirements, and prepare endpoints and keys.

*   [Requirements for Self-Hosted Standard Edition](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/self_hosted/stanctl/requirements.html)
*   [Requirements for Self-Hosted Custom Edition (Kubernetes or Red Hat OpenShift Container Platform)](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/backend_requirements.html)
*   [Requirements for Self-Hosted Classic Edition (Docker)](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/backend_requirements2.html)
*   [Instana agent requirements](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/agent_requirements.html)
*   [Instana sensor requirements](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/sensor_requirements.html)
*   [Outbound network access requirements: Self-hosted Instana deployments](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/self_hosted/docker_based/network-access.html)
*   [Preparing endpoints and keys](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/endpoints_and_keys.html)

1.  Install the Instana backend (Instana server):

*   For Standard Edition, see [Installing Self-Hosted Standard Edition](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/self_hosted/stanctl/overview.html).
*   For Custom Edition (Kubernetes or OpenShift Container Platform), see [Installing Self-Hosted Custom Edition (Kubernetes or Red Hat OpenShift Container Platform)](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/self_hosted/kubernetes_operator/index.html).
*   For Classic Edition (Docker), see [Installing Self-Hosted Classic Edition (Docker)](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/self_hosted/docker_based/index.html).

2.  Install Instana agents as described in the [Instana agent deployment](https://www.ibm.com/docs/en/instana-observability/current?topic=planning-deployment-options#instana-agent-deployment) section.
3.  Administer your Instana Tenant, such as onboarding users, managing API, agent keys, and role-based access control (RBAC), configuring user interface settings, and viewing audit logs. For more information, see Administer Instana.

##  Instana agent deployment

*   [Host agents](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/host_agent/index.html): A host agent runs on your host to collect and aggregate data from various sensors before it sends the data to the Instana backend. You can install the host agent on a virtual machine (VM), a physical host, Kubernetes, Cloud Foundry, VMware® Tanzu, or other similar platforms.
*   After you install the host agent, most Instana agent sensors, which are designed to monitor specific technologies, are automatically installed. Some sensors are also automatically configured after the host agent is installed. But for the other sensors, you need to do some configurations to make these sensors work. For the list of supported sensors, see [Agent sensors](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/ecosystem/index.html#agent-sensors).
*   [Cloud service agents](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/cloud_service_agents/index.html): These agents monitor services that are managed by cloud providers, like Amazon Relational Database Service (RDS) or Azure subscriptions.
    
*   [Serverless agents](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/serverless/index.html): These agents monitor AWS Lambda and other Serverless platforms.
    
*   [Website agent and mobile agents](https://www.ibm.com/docs/en/SSE1JP5_current/src/pages/setup_and_manage/web_and_mobile_app_agents/index.html): These agents monitor websites and mobile applications.
