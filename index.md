---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-12"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.IBM}} Marketplace. To see the documentation for the new version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/index.html){: new_window}.
{: tip}

# About
{: #wks_overview_full}

Use {{site.data.keyword.knowledgestudiofull}} to create a machine-learning model that understands the linguistic nuances, meaning, and relationships specific to your industry or to create a rule-based model that finds entities in documents based on rules that you define.
{: shortdesc}

To become a subject matter expert in a given industry or domain, {{site.data.keyword.watson}} must be trained. You can facilitate the task of training {{site.data.keyword.watson}} with {{site.data.keyword.watson}}&trade; {{site.data.keyword.knowledgestudioshort}}.

## Build a machine-learning model

{{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} provides easy-to-use tools for annotating unstructured domain literature, and uses those annotations to create a custom machine-learning model that understands the language of the domain. The accuracy of the model improves through iterative testing, ultimately resulting in an algorithm that can learn from the patterns that it sees and recognize those patterns in large collections of new documents. You can deploy the finished machine-learning model to other {{site.data.keyword.watson}} cloud-based offerings and cognitive solutions to find and extract mentions of relations and entities, including entity coreferences.

The following diagram illustrates how it works.

![Shows the process of building a model that can find entities and relations in new documents. ](images/wks-ovw-anno.png)

1. Based on a set of domain-specific source documents, the team creates a type system that defines entity types and relation types for the information of interest to the application that will use the model.
1. A group of two or more human annotators annotates a small set of source documents to label words that represent entity types, to identify relation types where the text identifies relationships between entity mentions, and to define coreferences, which identify different mentions that refer to the same thing, that is, the same entity. Any inconsistencies in annotation are resolved, and one set of optimally annotated documents is built, which forms the ground truth.
1. {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} uses the ground truth to train a model.
1. The trained model is used to find entities, relations, and coreferences in new, never-seen-before documents.

See [Creating a machine-learning annotator](/docs/services/knowledge-studio/ml-annotator.html) for more details.

## Build a rule-based model

{{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} provides a Rules editor that simplifies the process of finding and capturing common patterns in your documents as rules. You can then create a model that recognizes the rule patterns, and deploy it for use in other services.

See [Creating a rule-based annotator](/docs/services/knowledge-studio/rule-annotator.html) for more details.

## Watson services integration
{: #wks_watsoninteg}

Share domain artifacts and models between {{site.data.keyword.knowledgestudiofull}} and other {{site.data.keyword.watson}} services.

Use {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} to perform the following tasks:

- Import analyzed documents that are in [UIMA CAS XMI format](/docs/services/knowledge-studio/preannotation.html#wks_uimaweximport). For example, you can import UIMA CAS XMI files that were exported from {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer content analytics collections or [{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer Content Analytics Studio](/docs/services/knowledge-studio/preannotation.html#wks_uimawexstudio).
- Deploy a [machine-learning](/docs/services/knowledge-studio/publish-ml.html#wks_madiscovery) or [rule-based](/docs/services/knowledge-studio/rule-annotator-model-use.html#wks_rule_discovery) model to use with the {{site.data.keyword.watson}} {{site.data.keyword.discoveryshort}} service.
- Deploy a [machine-learning](/docs/services/knowledge-studio/publish-ml.html#wks_manlu) or [rule-based](/docs/services/knowledge-studio/rule-annotator-model-use.html#wks_rule_nlu) model to use with the {{site.data.keyword.nlushort}} service.
- [Export a machine-learning model](/docs/services/knowledge-studio/publish-ml.html#wks_maexport) to use in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.
- [Export a rule annotator PEAR file](/docs/services/knowledge-studio/rule-annotator-model-use.html#wks_rule_export) to use in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.
