---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-09"

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

On December 18, 2017, IBM launched {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud_notm}}, which marks the beginning of the process to migrate all {{site.data.keyword.knowledgestudioshort}} instances from {{site.data.keyword.IBM_notm}} Marketplace to the [{{site.data.keyword.cloud_notm}} platform ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}.
{: shortdesc}

**Note**: {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}} uses the term _workspace_, while {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace uses the term _project_. The functionality is the same. Only the terminology is different.

**Attention**: If you need to comply with GDPR, you must migrate to the {{site.data.keyword.cloud_notm}} platform. {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace has been retired and is not suitable for clients who require compliance with the European Union's General Data Protection Regulation (GDPR) (EU) 2016/679.

## Process
{: #process}

The migration process for your {{site.data.keyword.knowledgestudioshort}} projects depends on your {{site.data.keyword.IBM_notm}} Marketplace subscription, as shown in the following table.

| Subscription | Migration process | Details |
|------|-------------------|--------------------|
| Standard plan with a self-service subscription | Customer migrates instance and data | Migrate as soon as possible to gain access to the most up-to-date version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}.
| Standard plan with a subscription contract | {{site.data.keyword.IBM_notm}} migrates the subscription contract. Customer migrates the instance and data. | Contact your {{site.data.keyword.IBM_notm}} designated account representative or contact [{{site.data.keyword.cloud_notm}} Sales ![External link icon](../../icons/launch-glyph.svg "External link icon")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
| Premium plan with subscription contract | {{site.data.keyword.IBM_notm}} migrates the subscription contract. {{site.data.keyword.IBM_notm}} migrates the instance and data. | Contact your {{site.data.keyword.IBM_notm}} designated account representative or contact [{{site.data.keyword.cloud_notm}} Sales ![External link icon](../../icons/launch-glyph.svg "External link icon")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). |
{: caption="Table 1. Process and schedule to migrate {{site.data.keyword.knowledgestudioshort}} from {{site.data.keyword.IBM_notm}} Marketplace to {{site.data.keyword.cloud_notm}}" caption-side="top"}

## Self-migration of Standard plan instances
{: migratestandard}

If you have a Standard plan, complete the following steps to migrate your instance from {{site.data.keyword.IBM_notm}} Marketplace to {{site.data.keyword.cloud_notm}}:

1. If you don't have an {{site.data.keyword.cloud_notm}} account, sign up on [{{site.data.keyword.cloud_notm}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/registration/){: new_window} by using your {{site.data.keyword.ibmid}} from {{site.data.keyword.IBM_notm}} Marketplace.

   Your {{site.data.keyword.ibmid}} is the ID that you use to log in to {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace.

2. Log in to [{{site.data.keyword.cloud_notm}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net){: new_window}.
3. If your {{site.data.keyword.cloud_notm}} account is a Lite account, upgrade to a paid account. For more information about types of paid accounts, see [Account types ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/account/index.html){: new_window}.
4. From the [{{site.data.keyword.cloud_notm}} console ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/knowledge-studio){: new_window}, create a {{site.data.keyword.knowledgestudioshort}} Standard plan.
5. Follow the instructions on the screen, indicating that you want to migrate an instance from {{site.data.keyword.IBM_notm}} Marketplace to {{site.data.keyword.cloud_notm}}.
6. If you have more than one instance to migrate, repeat the process.

## Migration of Premium plan instances
{: migratesubscription}

If you have a {{site.data.keyword.knowledgestudioshort}} Premium plan, contact your {{site.data.keyword.IBM_notm}} designated account representative or contact [{{site.data.keyword.cloud_notm}} Sales ![External link icon](../../icons/launch-glyph.svg "External link icon")](mailto:watplat@us.ibm.com?subject=WKS Customer Migration). Once the subscription is migrated to {{site.data.keyword.cloud_notm}}, your data will be migrated by IBM on a schedule that is negotiated between you and {{site.data.keyword.IBM_notm}}.
