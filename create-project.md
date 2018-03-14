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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.IBM}} Marketplace. To see the documentation for the new version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/create-project.html){: new_window}.
{: tip}

# Creating a project
{: #create-project}

The first step in building a custom model is to create a project.
{: shortdesc}

## About this task

For each model that you want to build and use, you create a single project that contains the artifacts and resources needed to build the annotator component. You then train the annotator component to produce a custom model that can be deployed to an external service for use.

Before creating a project, answer these questions:

- **What type of model do you want to create?**

    - Machine-learning model: Uses statistical approach to finding entities and relationships in documents. This type of model can adapt as the amount of data grows.
    - Rule-based model: Uses a declarative approach to finding entities in documents. This type of model is more predictable, and is easier to comprehend and maintain. However, it does not learn from new data. It can only find patterns it has been taught to look for.

    > **Note:** You can also create one project that contains both one rule-based model and one machine-learning model.

- **What services will use the model?**

    See [{{site.data.keyword.watson}} services integration](/docs/services/knowledge-studio/index.html#wks_watsoninteg) for information about the other {{site.data.keyword.watson}} services that custom models can be used with.

## Procedure

To create a project, complete the following steps:

1. Log in as a {{site.data.keyword.watson}}&trade; {{site.data.keyword.knowledgestudioshort}} administrator, and click **Create Project**.

    > **Note:** People with the project manager role can perform almost all tasks except creating a project. An administrator must create the project initially and assign project managers to it.

1. Give the project a name. Choose a short name that reflects your domain content or the purpose of the annotator component. If you need to, you can change the project name later.
1. Identify the language of the documents in your project. The documents that you add to the project, and the dictionaries that you create or import, must be in the language that you specify.
1. Optional: If you want to change the tokenizer that is used by the application from the default machine learning-based tokenizer, then you can expand the **Advanced Options** section, and choose **Dictionary-based tokenizer**.

    The default tokenizer is more advanced than the dictionary-based tokenizer; it uses machine learning to identify the tokens in the source documents based on the statistical learning it has done in the language of the source documents. It identifies tokens with more precision because it understands the more natural and nuanced patterns of language. The dictionary-based tokenizer identifies tokens based on language rules. See [Tokenizers](/docs/services/knowledge-studio/create-project.html#wks_tokenizer) for more details.

1. Optional: If you want to add project managers to the project, then expand the **Advanced Options** section, and select the names of people you want to add as project managers from the list. The administrator can add or remove project managers later by editing the project.

    Only the names of people that you assigned to the project manager role from the User Account Management page for the instance are displayed. See [Assembling the team](/docs/services/knowledge-studio/team.html) for more information about adding users.

    > **Note:** If you have a free plan subscription, skip this step. You cannot add other users, so you cannot assign anyone to the project manager role. You do not need a separate project manager. As an administrator, you can perform all of the tasks that a project manager would typically perform.

1. Click **Create**.

## What to do next

After the project is created, you can start configuring the project resources.

To change the project description or project name, or to add or remove project managers later, an administrator can edit the project. From the {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} home page, click the **Show menu** icon on the project tile, and choose the **Edit** menu option.

**Related concepts**:

[Importing resources from another project](/docs/services/knowledge-studio/exportimport.html)

**Related reference**:

[Multiple language support](/docs/services/knowledge-studio/language-support.html)

## Tokenizers
{: #wks_tokenizer}

A tokenizer groups characters into tokens, and tokens into sentences. A token is loosely equivalent to a word.

The actions that a tokenizer must take to identify a document's tokens differ depending on the language of the document. In English, tokens are often equated to words as delimited by white spaces in a sentence. However, they do not always match one-to-one with words; other textual elements are considered tokens in some situations. For example, punctuation at the end of a sentence is considered a token, and contractions are often expanded into two tokens. In languages that do not use white spaces, such as Chinese, more complicated statistical algorithms are used to identify the tokens.

The tokenization process is important because it determines the groups of characters that users can highlight for annotation in the Ground Truth Editor. Annotations of entity and relation mentions are generally aligned with token boundaries, and must be labeled within a sentence; they cannot span sentence boundaries.

### Supported types

{{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} supports the following tokenizers:

- **Machine learning-based tokenizer (default)**

    This is a more advanced tokenizer that identifies the tokens in the source documents based on the statistical learning it has done in the language of the source documents. This tokenizer finds tokens that capture the more natural and nuanced patterns of language. You cannot customize this tokenizer.

- **Dictionary-based tokenizer**

    This tokenizer is based on linguistic dictionaries. It finds tokens that follow the rules of the source document language. Only advanced users can customize this tokenizer.

You must choose the tokenizer that you want to use when you create the project. You cannot switch to a different tokenizer later. For best results, use the default tokenizer. Only advanced users who want to modify the tokenizer behavior through a deterministic dictionary mechanism can choose the dictionary-based tokenizer. They can then customize it by adding new entries to the dictionary. However, customization must be done carefully because when you add new words to the dictionary, the changes can impact the machine-learning annotator in unintended ways.

## Summary of inputs, outputs, and limitations
{: #wks_formats}

Different stages of annotator component development require different inputs and produce different outputs.

For each stage of the annotator component development process, this table summarizes the typical activities that you perform, the supported input file formats, the outputs that can be produced, and any sizing limits or other requirements.

### All annotator component types

<table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d25459e252" class="stentry thleft thbot">Task</th>
<th valign="bottom" align="left" id="d25459e254" class="stentry thleft thbot">Typical usage</th>
<th valign="bottom" align="left" id="d25459e256" class="stentry thleft thbot">Supported input formats</th>
<th valign="bottom" align="left" id="d25459e258" class="stentry thleft thbot">Supported output formats</th>
<th valign="bottom" align="left" id="d25459e260" class="stentry thleft thbot">Limits and requirements</th>
</tr>
<tr class="strow"><td valign="top" headers="d25459e252" class="stentry"><p class="p wrapper">Type system management</p></td>
<td valign="top" headers="d25459e254" class="stentry"><p class="p wrapper">Create a type system or import and modify an existing type system.</p><p class="p">Define entity types
and relation types for your domain.</p>
<p class="p">You cannot see a visualization of the type
system.</p>
</td>
<td valign="top" headers="d25459e256" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">JSON file that you exported from a
Watson Knowledge
Studio project</p></li>
<li class="li"><p class="p wrapper">ZIP file that you exported from the Human Annotation Tool (HAT)</p></li>
</ul>
</td>
<td valign="top" headers="d25459e258" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">JSON</p></li>
</ul>
</td>
<td valign="top" headers="d25459e260" class="stentry"><p class="p wrapper">To avoid visual overload for human annotation, define no more than 50 entity types and 50
relation types.</p><p class="p">File size limitation for importing a type system: 20 MB</p>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e252" class="stentry"><p class="p wrapper">Dictionary management</p></td>
<td valign="top" headers="d25459e254" class="stentry"><p class="p wrapper">Import a CSV dictionary file in read-only mode or a ZIP of dictionaries that you exported
from another project.</p><p class="p">Create a new dictionary, and then import a CSV file of term entries or add
term entries to it.</p>
</td>
<td valign="top" headers="d25459e256" class="stentry"><p class="p wrapper">Dictionary file:</p><ul class="ul bullets"><li class="li"><p class="p wrapper">CSV file in UTF-8 format</p></li>
<li class="li"><p class="p wrapper">ZIP of dictionaries exported from another project</p></li>
</ul><p class="p wrapper">
Term entries file:</p><ul class="ul bullets"><li class="li"><p class="p wrapper">CSV file in UTF-8 format</p></li>
</ul>
</td>
<td valign="top" headers="d25459e258" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">CSV file in UTF-8 format</p></li>
<li class="li"><p class="p wrapper">ZIP of dictionaries to use in another project</p></li>
</ul>
</td>
<td valign="top" headers="d25459e260" class="stentry"><p class="p wrapper">File size limitations:</p><ul class="ul bullets"><li class="li"><p class="p wrapper">1 MB per CSV term entries file</p></li>
<li class="li"><p class="p wrapper">16 MB per CSV read-only dictionary file</p></li>
<li class="li"><p class="p wrapper">15,000 entries per dictionary, except a read-only dictionary</p></li>
<li class="li"><p class="p wrapper">64 dictionaries per project</p></li>
</ul>
</td>
</tr>
</table>

 {: #wks_formats__datasimpletable_xxj_qr5_2y}

### Machine-learning annotator component

<table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d25459e331" class="stentry thleft thbot">Task</th>
<th valign="bottom" align="left" id="d25459e333" class="stentry thleft thbot">Typical usage</th>
<th valign="bottom" align="left" id="d25459e335" class="stentry thleft thbot">Supported input formats</th>
<th valign="bottom" align="left" id="d25459e337" class="stentry thleft thbot">Supported output formats</th>
<th valign="bottom" align="left" id="d25459e339" class="stentry thleft thbot">Limits and requirements</th>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Document management </p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Import a small, representative subset of documents </p><p class="p">Import documents that contain
annotations previously added by a human annotator, a machine-learning annotator, or a 
UIMA
 analysis engine</p>
<p class="p">You
cannot ingest the entire corpus from 
IBM Watson Explorer
 for calculating high value documents for
annotation. </p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">CSV file in UTF-8 format</p></li>
<li class="li"><p class="p wrapper">DOCXML file in UTF-8 format</p></li>
<li class="li"><p class="p wrapper">Text in UTF-8 format</p></li>
<li class="li"><p class="p wrapper">ZIP file that contains documents exported from another corpus</p></li>
<li class="li"><p class="p wrapper">ZIP file that contains documents in
UIMA CAS XMI format</p></li>
</ul>
</td>
<td valign="top" headers="d25459e337" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">ZIP archive file of documents</p></li>
</ul>
</td>
<td valign="top" headers="d25459e339" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">40,000 characters per document</p></li>
<li class="li"><p class="p wrapper">10,000 documents per project</p></li>
<li class="li"><p class="p wrapper">1,000 document sets (including annotation sets) per project</p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Pre-annotation</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Use a dictionary to
provide a starting point for human annotation.</p><p class="p">You cannot re-annotate a corpus from
IBM Watson Discovery Advisor
 or
IBM Watson Explorer
.</p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">Raw documents. </p><p class="p wrapper"><b>Note:</b> Do not pre-annotate documents that a human annotator has already
annotated, or you will lose the work done by the human annotator.</p>
</td>
<td valign="top" headers="d25459e337" class="stentry"><p class="p wrapper">Partly-annotated documents</p></td>
<td valign="top" headers="d25459e339" class="stentry"><p class="p wrapper">None</p></td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Document annotation</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Manage human annotation</p><p class="p">Annotate entities, relations, and coreference chains to create
ground truth</p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">Annotation task</p></td>
<td valign="top" headers="d25459e337" class="stentry"><p class="p wrapper">Ground truth</p></td>
<td valign="top" headers="d25459e339" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">256 active annotation tasks per project</p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Training and refinement</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Train a supervised machine-learning annotator to extract domain-specific information from
unstructured text.</p><p class="p">Evaluate and improve a supervised machine-learning annotator.</p>
<p class="p">You cannot
create a semi-supervised or unsupervised machine-learning annotator.</p>
<p class="p">You cannot
do extensive feature engineering.</p>
</td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">Not applicable</p></td>
<td valign="top" headers="d25459e337" class="stentry"><p class="p wrapper">Machine-learning model</p></td>
<td valign="top" headers="d25459e339" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">1 machine-learning annotator component per project</p></li>
<li class="li"><p class="p wrapper">10 annotator component versions per project</p></li>
<li class="li"><p class="p wrapper">Maximum number of projects is determined by your subscription plan.</p></li>
<li class="li"><p class="p wrapper">The maximum number of training actions you can perform per month is determined by your subscription plan. </p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e331" class="stentry"><p class="p wrapper">Publication</p></td>
<td valign="top" headers="d25459e333" class="stentry"><p class="p wrapper">Publish a machine-learning annotator to use for performing text extraction in other
Watson applications. </p></td>
<td valign="top" headers="d25459e335" class="stentry"><p class="p wrapper">Not applicable</p></td>
<td valign="top" headers="d25459e337" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">model ID (for use in
AlchemyLanguage
 or
Watson Discovery
 services) </p></li>
<li class="li"><p class="p wrapper">ZIP file (for use in
IBM Watson Explorer
)</p></li>
</ul>
</td>
<td valign="top" headers="d25459e339" class="stentry">
  <p class="p">To deploy into AlchemyLanguage,
    you must have a valid AlchemyLanguage
    Advanced plan key ID.</p>
  <p class="p">To deploy to Watson Discovery
    service, you must know the service
    {{site.data.keyword.Bluemix}} space and instance names.</p>
</td>
</tr>
</table>

### Rule-based annotator component

<table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable"><tr class="sthead"><th valign="bottom" align="left" id="d25459e509" class="stentry thleft thbot">Task</th>
<th valign="bottom" align="left" id="d25459e511" class="stentry thleft thbot">Typical usage</th>
<th valign="bottom" align="left" id="d25459e513" class="stentry thleft thbot">Supported input formats</th>
<th valign="bottom" align="left" id="d25459e515" class="stentry thleft thbot">Supported output formats</th>
<th valign="bottom" align="left" id="d25459e517" class="stentry thleft thbot">Limits and requirements</th>
</tr>
<tr class="strow"><td valign="top" headers="d25459e509" class="stentry"><p class="p wrapper">Rule editor</p></td>
<td valign="top" headers="d25459e511" class="stentry"><p class="p">Create or import documents to the Rules editor from which to define classes, regular expressions,
and rules.</p>
</td>
<td valign="top" headers="d25459e513" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">Plain text (added in editor)</p></li>
<li class="li"><p class="p wrapper">CSV file in UTF-8 format</p></li>
<li class="li"><p class="p wrapper">Copied from the All document set</p></li>
</ul>
</td>
<td valign="top" headers="d25459e515" class="stentry"><p class="p wrapper">None</p></td>
<td valign="top" headers="d25459e517" class="stentry"><ul class="ul bullets">
<li class="li"><p class="p wrapper">1 rule-based annotator component per project</p></li>
<li class="li"><p class="p wrapper">5,000 characters per document</p></li>
<li class="li"><p class="p wrapper">100 documents per project</p></li>
<li class="li"><p class="p wrapper">Maximum size of document title is 256 characters</p></li>
<li class="li"><p class="p wrapper">200 rules per project</p></li>
<li class="li"><p class="p wrapper">400 classes per project</p></li>
<li class="li"><p class="p wrapper">100 regular expression group per project</p></li>
<li class="li"><p class="p wrapper">100 regular expression entries per regular expression group</p></li>
<li class="li"><p class="p wrapper">1,000 characters per regular expression entry</p></li>
<li class="li"><p class="p wrapper">5 rule annotator model versions per project</p></li>
</ul>
</td>
</tr>
<tr class="strow"><td valign="top" headers="d25459e509" class="stentry"><p class="p wrapper">Publication</p></td>
<td valign="top" headers="d25459e511" class="stentry"><p class="p wrapper">Publish a rule-based model to use for performing pattern recognition in other
Watson applications.</p></td>
<td valign="top" headers="d25459e513" class="stentry"><p class="p wrapper">Not applicable</p></td>
<td valign="top" headers="d25459e515" class="stentry"><ul class="ul bullets"><li class="li"><p class="p wrapper">model ID (for use in
AlchemyLanguage
 or
Watson Discovery
 services) </p></li>
</ul>
</td>
<td valign="top" headers="d25459e517" class="stentry">
  <p class="p">To deploy into AlchemyLanguage,
    you must have a valid AlchemyLanguage
    Advanced plan key ID.</p>
  <p class="p">To deploy to Watson Discovery
    service, you must know the service {{site.data.keyword.Bluemix_notm}}
    space and instance names.</p>
</td>
</tr>
</table>
