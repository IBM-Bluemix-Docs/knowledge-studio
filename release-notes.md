---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-15"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.IBM}} Marketplace. To see the documentation for the new version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/docs/services/watson-knowledge-studio/release-notes.html){: new_window}.
{: tip}

# Release notes
{: #release-notes}

The following new features and changes to {{site.data.keyword.knowledgestudiofull}} are available.
{: shortdesc}

## August 2018
{: #august2018}

### New features and changes
{: #new-august2018}

- Introduced a new option for automated migration of Standard plan instances from the deprecated {{site.data.keyword.IBM_notm}} Marketplace platform to the [{{site.data.keyword.cloud_notm}} platform ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}. If you have a Standard instance on the deprecated platform, you'll have the option to migrate. For more information, see [Migrating to {{site.data.keyword.cloud_notm}}](/docs/services/knowledge-studio/client-migration.html).

## March 2018
{: #march2018}

### Changes
{: #new-march2018}

- {{site.data.keyword.alchemylanguagefull}} is no longer available as a pre-annotator. If you migrate to {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud}}, you can use {{site.data.keyword.nlushort}} to pre-annotate your documents. For information about migrating to {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud}}, see [Migrating to {{site.data.keyword.cloud}}](/docs/services/knowledge-studio/client-migration.html#migrate)

## November 2017
{: #november2017}

### Changes
{: #new-november2017}

- Fixed an issue where some relation annotations were missing in the exported corpus.
- Fixed an issue where a model could not be withdrawn from deployment if its status was **None**.
- Fixed an issue where the model could not be evaluated for Korean.

## October 2017
{: #october2017}

### Changes
{: #new-october2017}

- Fixed the issue with the **Export** button not being enabled until you refreshed the browser window in the {{site.data.keyword.Bluemix_notm}} [experimental](/docs/services/knowledge-studio/troubleshooting.html#experimental) release.
- Fixed the button labels and tooltips to match the changes for the terms _upload_ and _download_ in the {{site.data.keyword.Bluemix_notm}} [experimental](/docs/services/knowledge-studio/troubleshooting.html#experimental) release. These terms  are used instead of _import_ and _export_ when referring to type systems, documents, and dictionaries.
- Fixed the delay in updating the descriptions on the {{site.data.keyword.knowledgestudioshort}} User Account Management page in the {{site.data.keyword.Bluemix_notm}} [experimental](/docs/services/knowledge-studio/troubleshooting.html#experimental) release.
- In the pre-annotation section of the interface, made a couple GUI changes to clarify the functionality of the machine learning model, the rule-based model, the dictionary, and {{site.data.keyword.alchemylanguagefull}}. Changed the button label from **Run** to **Pre-annotate**, changed the title of the window from **Run Annotator** to **Run Pre-annotation**, and changed the error message to clarify that you can't add automated annotations after humans annotated the documents.
- For projects or workspaces that use dictionary-based tokenizers, fixed an issue that showed empty sentences if you imported documents without ground truth.

## September 2017
{: #september2017}

### New features and changes
{: #new-sept17}

- Released a new front-end user experience for {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.Bluemix}} as an [experimental](/docs/services/knowledge-studio/troubleshooting.html#experimental) service. Changes include a reorganized navigation and a new model performance analysis page. For a summary of the navigation changes, see the table in the known issues.
- Added Chinese (simplified) and Dutch language support.

### Known issues
{: #issues-sept17}

- For a rule-based model, after you map classes and entity types, the **Export** button is not enabled until you refresh the browser window.
- For the {{site.data.keyword.Bluemix_notm}} [experimental](/docs/services/knowledge-studio/troubleshooting.html#experimental) release, some of the documentation terminology does not match the new interface. The documentation matches the interface in {{site.data.keyword.IBM_notm}} Marketplace. The following terms have changed in the [experimental](/docs/services/knowledge-studio/troubleshooting.html#experimental) release:

| Term in {{site.data.keyword.IBM_notm}} Marketplace | Term in {{site.data.keyword.Bluemix_notm}} | Notes |
|----------|----------|----------|
| _project_ | _workspace_ | This term was changed because {{site.data.keyword.Bluemix_notm}} also uses the term _project_ |
| _import_ and _export_ | _upload_ and _download_ | The terms _import_ and _export_ are now referred to as _upload_ and _download_ when used in terms of documents and entity types. The term _export_ is still used when referring to exporting a model to applications such as {{site.data.keyword.watson}} Explorer. |
{: caption="Table 1. Terminology changes for {{site.data.keyword.Bluemix_notm}} version" caption-side="top"}

- For the {{site.data.keyword.Bluemix_notm}} [experimental](/docs/services/knowledge-studio/troubleshooting.html#experimental) release, some of the documentation task steps do not match the new interface. The documentation matches the interface in {{site.data.keyword.IBM_notm}} Marketplace. The following table summarizes the navigation changes for the [experimental](/docs/services/knowledge-studio/troubleshooting.html#experimental) release:

| Feature | {{site.data.keyword.IBM_notm}} Marketplace location | {{site.data.keyword.Bluemix_notm}} location
|----------|----------|----------|
|Annotator Component tab | Main navigation | No longer exists |
|Confusion Matrix table (from the Statistics tab) | Annotator Component > Details | Model Management > Performance > Detailed Statistics link |
|Dictionaries tab | Main navigation | Assets & Tools > Pre-annotators |
|Dictionary Mapping page | Annotator Component | Assets & Tools > Pre-annotators |
|Entity Types tab | Type System | Assets & Tools > Entity Types |
|Ground Truth Editor | Human Annotation | Document Annotation tab |
|Ground Truth Editor Settings tab | Human Annotation | Settings > Document Annotation Settings |
|Models, running and exporting | Annotator Component | Model Management > Versions |
|Rules tab | Main navigation | Document Annotation > Rules |
|Statistics tab | Annotator Component > Details | Model Management > Performance |
|Summary table (from the Statistics tab) | Annotator Component > Details | Model Management > Performance > Detailed Statistics link |
|Type Mapping tab (for the rule-based model) | Annotator Component > Details | Model Management > Versions > Rule-based model type mapping |
{: caption="Table 2. Navigation changes for {{site.data.keyword.Bluemix_notm}} version" caption-side="top"}

## July 2017
{: #july2017}

- Fixed a defect that, in some cases, caused the header to disappear
- Applied security updates for infrastructure components

## June 2017
{: #june2017}

- Improved stability for handling large data under certain conditions
- Fixed a defect for an adjudication error

## May 2017
{: #may2017}

- Added ability to rename various objects, such as projects, document sets, and so on
- Added ability to deploy NLU models to specific {{site.data.keyword.Bluemix}} regions
- Improved performance for displaying large table for IAA
- Fixed minor defects
- Applied security fixes

## April 2017
{: #april2017}

- Improved stability for {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} Premium
- Added usage analysis for business metrics

## Releases prior to April 2017

See [{{site.data.keyword.IBM_notm}} tech note #1986001 ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/support/docview.wss?uid=swg21986001){: new_window}.
