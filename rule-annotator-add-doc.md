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

# Adding documents for defining rules
{: #wks_rule_anno_add}

Add documents with linguistic patterns that illustrate the types of rules you want to define.
{: shortdesc}

Documents that you add for defining rules are kept separate from documents that you add for annotation. Their sole purpose is to be used for mining examples of patterns. They are not used for training nor are they ever exported.

## Ways you can add documents to the rule editor

- **Author a text document in UTF-8 format**

    You can add text that illustrates a pattern directly into the rule editor. The name that you specify for the document cannot be longer than 256 characters.

- **Import a CSV file**

    Import a file in CSV format that contains the document text.

- **Copy a document that was imported for annotation**

    If a document that is part of a set that was imported for annotation purposes contains examples of patterns that you want to capture as rules, you can copy the document over to the rule editor. Any changes that you make to the document do not impact the original version of the document that is being used for annotation. See [Adding documents to a project](/docs/services/knowledge-studio/documents-for-annotation.html#wks_projadd) for information about importing documents.

For documents that you copy or import, choose documents that contain distinct patterns that help to identify entity types in documents.
