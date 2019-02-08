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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.IBM}} Marketplace. To see the documentation for the new version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/docs/services/watson-knowledge-studio/train-ml.html){: new_window}.
{: tip}

# Training the machine-learning annotator
{: #train-ml}

In {{site.data.keyword.knowledgestudiofull}} , the creation of the machine-learning annotator component involves training the machine-learning annotator and evaluating how well the annotator performed when annotating test data and blind data.
{: shortdesc}

## Creating a machine-learning annotator component
{: #wks_madocsets}

When you create a machine-learning annotator component, you select the document sets that you want to use to train the annotator component and specify the percentage of documents that are to be used as training data, test data, and blind data.

### About this task

By exploring the performance metrics, you can identify ways to improve the annotator component's accuracy.

> **Restriction:** Only three machine-learning annotators can be trained at a time per {{site.data.keyword.watson}}&trade; {{site.data.keyword.knowledgestudioshort}} instance. If your instance contains multiple projects and the number of machine-learning annotators that are being trained in other projects totals 3 already, then your request to train the machine-learning annotator in your project will be queued until the other training processes are done.

### Procedure

To create a machine-learning annotator component:

1. Log in as a {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} administrator and open the **Human Annotation** page.
1. Verify that all of the document sets have been approved and that all annotation conflicts have been resolved through adjudication. Only documents that have become ground truth through adjudication or approval can be used to train the annotator component.
1. Open the **Annotator Component** page. Under the **Machine Learning** annotator type, click **Create this type of annotator**.
1. Select the document sets that you want to use for training the annotator.

    > **Note:** The document sets must contain at least 10 annotated documents.

1. Specify how you want to allocate documents from your document sets to be used by the system-level training, test, or blind sets.

    See [Document set management](/docs/services/knowledge-studio/improve-ml.html#wks_mamanagedata) for help determining which ratios to apply.

1. Optional: Associate any dictionaries that you want the machine-learning annotator to use during training with the entity type of the dictionary entries.

    If you created a dictionary pre-annotator, then you already performed this step. Click **Reuse mapping that is defined for dictionary pre-annotator** to reuse it or define a new mapping.

    The annotator uses the type information of dictionary terms as one feature among many linguistic analysis features that it considers during training.

1. Click **Train** to train the annotator, or click **Train &amp; Evaluate** to train the annotator, evaluate annotations added by the machine-learning annotator, and analyze the performance statistics.

    > **Important:** Training a machine-learning annotator can take several minutes or several hours, depending on the number of human annotations that exist and the total number of words across all documents.

1. After the annotator component is created, select one of the following actions:

    <table border="1" frame="hsides" rules="rows" cellpadding="4" cellspacing="0" summary="Each row in this table describes one option for a choice." class="simpletable choicetable choicetableborder">
      <thead><tr><th id="d33883e137-option" valign="bottom" align="left" class="ncol thleft thbot">Option</th>
          <th id="d33883e137-desc" valign="bottom" align="left" class="ncol thleft thbot">Description</th></tr></thead>
      <tbody><tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e139" class="stentry choption ncol"><p class="p wrapper"><strong>Log</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e139" class="stentry chdesc ncol"><p class="p wrapper">View the log file to see whether any problems occurred.</p></td>
        </tr>
        <tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e144" class="stentry choption ncol"><p class="p wrapper"><strong>Details</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e144" class="stentry chdesc ncol"><p class="p wrapper">View the annotation performance statistics, change the document sets that you want to use
              for training and testing the annotator, and create snapshot versions of the annotator component
              artifacts.</p></td>
        </tr>
        <tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e149" class="stentry choption ncol"><p class="p wrapper"><strong>Export</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e149" class="stentry chdesc ncol"><p class="p wrapper">Export a <code>ZIP</code> file to your local system that contains the components
              that are required for the annotator to run in a machine-learning runtime environment.</p></td>
        </tr>
      </tbody>
    </table>

## Evaluating annotations added by the annotator component
{: #wks_matest}

You can compare the ground truth view for annotations added by human annotators to the annotations added by the annotator component.

### Procedure

To evaluate the annotations added by the annotator component:

1. On the **Annotator Component** page, locate the annotator component that you created and click **Details**. The Training/Test/Blind page is displayed.
1. Click **View Ground Truth** for the training set or test set to see the annotations that were added through pre-annotation and by human annotators. The Ground Truth Editor opens. Click to open individual documents and see how the mentions, relations, and coreferenced mentions were annotated.
1. Click **View Decoding Results** to see the annotations that the machine-learning annotator added to documents in the test set. This button is available only after you evaluate the annotator component, either by clicking **Train &amp; Evaluate** on this page or when you created the annotator component, or by clicking **Evaluate** on this page. By viewing results, you can see how well the machine-learning annotator labeled mentions, relations, and coreferenced mentions in the test data.
1. If you want to change how the documents are divided between training, test, and blind data sets, click **Edit Sets**. For example, if initial results seem acceptable, you might want to increase the number of documents in the test set to further test the machine-learning annotator's results. You can change the ratio for how documents are automatically divided for different purposes, or you can select specific document sets to use as training data, test data, and blind data.
1. If you made any changes, click **Train &amp; Evaluate** to retrain the annotator component and re-evaluate the annotations.

## Deleting a machine-learning annotator
{: #wks_madelete}

You cannot delete a machine-learning annotator.

You can delete the project that was used to develop the annotator component, but you cannot delete the annotator itself. Deleting an annotator is not the best approach. Instead, update or replace the artifacts that are used to train the model. Even if the model is not producing the results you expect, you can continue to refine it. Each time you create a new version, the model is built anew. You can edit artifacts like dictionaries and the type system, and choose to use different annotation sets when you train the next version.
