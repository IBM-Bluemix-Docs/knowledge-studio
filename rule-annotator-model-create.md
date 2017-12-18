---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-14"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.IBM}} Marketplace. To see the documentation for the new version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/rule-annotator-model-create.html){: new_window}.
{: tip}

# Creating the rule-based model
{: #wks_rule_train}

After defining rules, you can create a rule-based model.
{: shortdesc}

## Procedure

To create a rule-based model. complete the following steps:

1. Log in as a {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} administrator or project manager and open the **Annotator Component** page.
1. If you already created an annotator, then click **Create Annotator**. Otherwise, on the **Rule** annotator tile, click **Create this type of annotator**.
1. Map the entity types from your type system to one or more classes that you used to define rules.
1. Click **Create** &gt; **Create &amp; Run** .

## Deleting a rule annotator
{: #wks_rule_delete_model}

You cannot delete a rule annotator.

You can delete the project that was used to develop the rule annotator component, but you cannot delete the annotator itself. Deleting an annotator is not the best approach. Instead, recreate the rules that are defined for it. Editing the rules directly changes the behavior of the rule-based model.
