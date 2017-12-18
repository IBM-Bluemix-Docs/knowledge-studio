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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.IBM}} Marketplace. To see the documentation for the new version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/exportimport.html){: new_window}.
{: tip}

# Importing resources from another project
{: #exportimport}

To accelerate the creation of an annotator component, you can import resources like documents (with or without ground truth annotations), a type system, and dictionaries that you exported from another project.
{: shortdesc}

The ability to separately export and import different resources gives you flexibility when designing and creating an annotator component. For example, you might create one project to design the type system and perform human annotation, and then create a separate project, perhaps in a separate instance of {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} with different users, to train the machine annotator. Being able to import the resources, including the ground truth created by human annotators, makes this scenario possible.

You cannot export and import a machine-learning model. Instead, you can export all of the artifacts that were used to create the annotator from one project and import them into a new project. From the new project, you can run training again to recreate the model. The new model should produce similar results to the original model because they were both trained with the same set of artifacts.

The files that you export are operating system-independent. The {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} instances where you export and import files do not have to run the same version of Linux.

## Type systems
{: #wks_exportimport_expimp_type}

To export a type system, open the **Type System** page and click **Export**. The system creates a file named `types-ID.json` and prompts you to download the file to your local system. To use this type system in a new project, open the **Type System** page and import the `JSON` file that you exported.

## Dictionaries
{: #wks_exportimport_expimp_dict}

To export one or more dictionaries, open the **Dictionaries** page, select the dictionaries that you want to export, and click **Export**. For each dictionary that you select, the system creates a file named `dictionary name_timestamp.csv`, combines the files into a `ZIP` file named `project name_dictionary_timestamp.zip`, and prompts you to download the file to your local system. You can also export an individual dictionary by opening the dictionary and clicking **Export**. Preview-only dictionaries that you imported as a dictionary CSV file cannot be exported.

Before you import an exported dictionary into a new project, you must export the type system from the old project and import it into the new project. The type system and dictionaries must originate from the same {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} project, and the type system must exist in the new project before you import the dictionaries.

To import dictionaries, open the **Dictionaries** page and either add a `CSV` file that you exported or import the `ZIP` file.

## Documents
{: #wks_exportimport_expimp_doc}

To export documents that you added to the corpus, open the **Documents** page and click **Export**. The system creates a file named `corpus-ID.zip` and prompts you to download the file to your local system. The `ZIP` file contains all documents in the corpus. Annotations that were added to annotation sets are included in the ZIP file, but only after the annotation sets have been approved and promoted to ground truth.

> **Restriction:** Any documents that were pre-annotated with {{site.data.keyword.alchemylanguageshort}} will be obscured into a non-readable format when they are exported. Even annotations in those documents that were added by human annotation are unreadable.

Before you import documents that include ground truth into a new project, you must export the type system from the old project and import it into the new project. The type system and documents must originate from the same {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} project, and the type system must exist in the new project before you import the ground truth annotations.

To import documents, open the **Documents** page in the new project and select the corpus `ZIP` file that you exported. Specify whether you want the imported documents to include or exclude the ground truth annotations before you click **Import**. Only annotations that were promoted to ground truth before the documents were exported will be imported.

**Related concepts**:

[Type systems](/docs/services/knowledge-studio/artifacts.html#wks_typesystem)

[Dictionaries](/docs/services/knowledge-studio/artifacts.html#wks_dictionaries)

[Documents for machine-learning annotators](/docs/services/knowledge-studio/documents-for-annotation.html#wks_t_docs_intro)

[Documents for rule-based annotators](/docs/services/knowledge-studio/rule-annotator-add-doc.html)
