---

copyright:
  years: 2015, 2017
lastupdated: "2017-09-22"

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

# Release notes
{: #release-notes}

The following new features and changes to {{site.data.keyword.knowledgestudiofull}} are available.
{: shortdesc}

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
