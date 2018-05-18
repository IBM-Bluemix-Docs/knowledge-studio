---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.IBM}} Marketplace. To see the documentation for the new version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/client-migration.html){: new_window}.
{: tip}

# Migrating to IBM Cloud
{: #migrate}

On December 18, 2017, IBM launched {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud_notm}}, which marks the beginning of the process to migrate all {{site.data.keyword.knowledgestudioshort}} instances from {{site.data.keyword.IBM_notm}} Marketplace to {{site.data.keyword.cloud_notm}}.
{: shortdesc}

**Note**: {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}} uses the term _workspace_, while {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace uses the term _project_. The functionality is the same. Only the terminology is different.

## Process and schedule
{: #process}

The migration process and schedule for your {{site.data.keyword.knowledgestudioshort}} projects depends on your current [pricing plan on {{site.data.keyword.IBM_notm}} Marketplace ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top){: new_window} and account type, as shown in the following table:

| Plan and account | Migration process | Migration schedule |
|------|-------------------|--------------------|
| Free plan | Customer migrates instance and data | Migrations must be complete on or before February 1, 2018. On February 2, 2018, all Free plans on {{site.data.keyword.IBM_notm}} Marketplace will be purged, including associated project data. |
| Standard plan with Pay-As-You-Go account | Customer migrates instance and data | Migrations must be complete on or before June 29, 2018. On June 30, 2018, all Standard plans with Pay-As-You-Go accounts on {{site.data.keyword.IBM_notm}} Marketplace will be purged, including associated project data.
| Standard plan on contract | Customer migrates instance and data. {{site.data.keyword.IBM_notm}} renews contract. | Migrations must be complete on or before June 29, 2018. Contact your {{site.data.keyword.IBM_notm}} designated account representative or contact [{{site.data.keyword.cloud_notm}} Sales ![External link icon](../../icons/launch-glyph.svg "External link icon")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
| Premium plan on contract | {{site.data.keyword.IBM_notm}} migrates instance and data. {{site.data.keyword.IBM_notm}} renews contract. | Migrations must be complete on or before June 29, 2018. Contact your {{site.data.keyword.IBM_notm}} designated account representative or contact [{{site.data.keyword.cloud_notm}} Sales ![External link icon](../../icons/launch-glyph.svg "External link icon")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
{: caption="Table 1. Process and schedule to migrate {{site.data.keyword.knowledgestudioshort}} from {{site.data.keyword.IBM_notm}} Marketplace to {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Migration of Free plans
{: migratefree}

If you have a {{site.data.keyword.knowledgestudioshort}} Free plan, complete the following steps to migrate your instance and projects from {{site.data.keyword.IBM_notm}} Marketplace to {{site.data.keyword.cloud_notm}}:

1. If you don't have an {{site.data.keyword.cloud_notm}} account, sign up on [{{site.data.keyword.cloud_notm}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/wks_cloud){: new_window} by using your {{site.data.keyword.ibmid}} from {{site.data.keyword.IBM_notm}} Marketplace.

   Your {{site.data.keyword.ibmid}} is the ID that you use to log in to {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace.

1. Log in to [{{site.data.keyword.cloud_notm}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net){: new_window}.
1. If you don't have a {{site.data.keyword.knowledgestudioshort}} instance on {{site.data.keyword.cloud_notm}}, create one on the [{{site.data.keyword.cloud_notm}} catalog {{site.data.keyword.knowledgestudioshort}} page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Follow the [backup and restore](/docs/services/knowledge-studio/backup-restore.html) process to manually migrate your projects from the {{site.data.keyword.IBM_notm}} Marketplace instance to your instance on {{site.data.keyword.cloud_notm}}.

  **Note**: If you have a model that is already deployed and you plan to delete the workspace after you back it up, withdraw the model from deployment. You can rebuild and redeploy the model after you restore the workspace from the backup. For information about undeploying models on {{site.data.keyword.cloud_notm}}, see [Undeploying machine learning models ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model){: new_window} and [Undeploying rule-based models ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model){: new_window}.

## Migration of Standard plans for Pay-As-You-Go accounts
{: migratepaygo}

If you have a Standard plan and a [Pay-As-You-Go ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/pricing/billable.html){: new_window} account, complete the following steps to migrate your instance and projects from {{site.data.keyword.IBM_notm}} Marketplace to {{site.data.keyword.cloud_notm}}:

1. If you don't have an {{site.data.keyword.cloud_notm}} account, sign up on [{{site.data.keyword.cloud_notm}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/){: new_window} by using your {{site.data.keyword.ibmid}} from {{site.data.keyword.IBM_notm}} Marketplace.

   Your {{site.data.keyword.ibmid}} is the ID that you use to log in to {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace.

1. Log in to [{{site.data.keyword.cloud_notm}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net){: new_window}.
1. If you don't have a {{site.data.keyword.knowledgestudioshort}} instance on {{site.data.keyword.cloud_notm}}, create one on the [{{site.data.keyword.cloud_notm}} catalog {{site.data.keyword.knowledgestudioshort}} page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Follow the [backup and restore](/docs/services/knowledge-studio/backup-restore.html) process to manually migrate your projects from the {{site.data.keyword.IBM_notm}} Marketplace instance to your instance on {{site.data.keyword.cloud_notm}}.

  **Note**: If you have a model that is already deployed and you plan to delete the workspace after you back it up, withdraw the model from deployment. You can rebuild and redeploy the model after you restore the workspace from the backup. For information about undeploying models on {{site.data.keyword.cloud_notm}}, see [Undeploying machine learning models ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model){: new_window} and [Undeploying rule-based models ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model){: new_window}.

## Migration of Standard plans for contract accounts
{: migratecontract}

If you have a {{site.data.keyword.knowledgestudioshort}} Standard plan on contract, complete the following steps to renew your contract and migrate your instance and projects from {{site.data.keyword.IBM_notm}} Marketplace to {{site.data.keyword.cloud_notm}}:

1. To renew your contract, contact your {{site.data.keyword.IBM_notm}} designated account representative or contact [{{site.data.keyword.cloud_notm}} Sales ![External link icon](../../icons/launch-glyph.svg "External link icon")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration).
1. After you renew your contract on {{site.data.keyword.cloud_notm}}, log in to [{{site.data.keyword.cloud_notm}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net){: new_window}.
1. If you don't have a {{site.data.keyword.knowledgestudioshort}} instance on {{site.data.keyword.cloud_notm}}, create one on the [{{site.data.keyword.cloud_notm}} catalog {{site.data.keyword.knowledgestudioshort}} page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}.
1. Follow the [backup and restore](/docs/services/knowledge-studio/backup-restore.html) process to manually migrate your projects from the {{site.data.keyword.IBM_notm}} Marketplace instance to your instance on {{site.data.keyword.cloud_notm}}.

  **Note**: If you have a model that is already deployed and you plan to delete the workspace after you back it up, withdraw the model from deployment. You can rebuild and redeploy the model after you restore the workspace from the backup. For information about undeploying models on {{site.data.keyword.cloud_notm}}, see [Undeploying machine learning models ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model){: new_window} and [Undeploying rule-based models ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model){: new_window}.

## Migration of Premium plans for contract accounts
{: migratecontract}

If you have a {{site.data.keyword.knowledgestudioshort}} Premium plan on contract, contact your {{site.data.keyword.IBM_notm}} designated account representative or contact [{{site.data.keyword.cloud_notm}} Sales ![External link icon](../../icons/launch-glyph.svg "External link icon")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). Once the contract is renewed on {{site.data.keyword.cloud_notm}}, your data will be migrated by IBM on a schedule that is negotiated between you and {{site.data.keyword.cloud_notm}}.
