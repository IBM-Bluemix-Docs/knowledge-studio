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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.IBM}} Marketplace. To see the documentation for the new version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/improve-ml.html){: new_window}.
{: tip}

# Making machine-learning model improvements
{: #improve-ml}

After you determine areas in which the annotator is having trouble, take steps to improve its performance.
{: shortdesc}

## Creating annotator component versions
{: #wks_maversions}

After you create a machine-learning annotator component, you can take a snapshot to keep a backup version of the current resources in case you want to restore the resources in a future iteration.

### About this task

The F1 score provides an indication of the quality of the annotator component. If the annotator component performance results are good, you might want to store a version of the component before changing any of the resources. If changes that you make result in poorer quality, you can revert to a version that you stored. When you revert to an older version, all annotation tasks are archived because they are no longer valid.

You can have a maximum of 10 versions of a project. If you reach that limit, delete older versions or versions that you no longer need before creating a new version.

When you create a new version, the following resources are captured:

- Type system
- Corpus
- Ground truth
- Machine-learning model
- Machine-learning model evaluation results

The following resources are excluded:

- Annotation tasks, because they are temporal by design, used only for determining ground truth
- Dictionaries, because dictionaries can be large, and various types of dictionaries are managed in different ways

### Procedure

To create and restore machine-learning annotator component versions:

1. Log in as a {{site.data.keyword.watson}}&trade; {{site.data.keyword.knowledgestudioshort}} administrator or project manager, open the **Annotator Component** page, click **Details**, and then click **Versions**. Performance statistics about the current (first) version, labeled version 1.0, are displayed.
1. To take a snapshot of the current version, click **Take Snapshot**. The resources in version 1.0 are frozen, and a new version, labeled 1.1, becomes the current version. For each new version that you create, the minor version number is incremented, for example, 1.0 becomes 1.1 and then becomes 1.2.
1. Revise the project resources as needed, re-train, and re-evaluate the annotator component.
1. If you are pleased with the performance results and want to store the new version before making future changes, create another version. Continue revising resources and re-training the annotator component as needed, creating a new version for each iteration that you want to retain.
1. If performance results are worse, and you want to revert to a previous version before testing any further:

    1. Open the **Dictionaries** page and export any dictionaries that you want to re-use in the restored annotator component.
    1. Return to the **Versions** page and click **Promote** for the version that you want to restore. The version that you promote becomes the current version, and the version number changes to 2.0. When you promote a version, the major version number is incremented and the minor version number becomes 0, for example, 1.1 becomes 2.0.
    1. Open the **Dictionaries** page and import the dictionaries that you exported.
    1. If testing of the new version requires changes to ground truth, open the **Human Annotation** page and create a new annotation task.

## Modifying a type system without losing human annotations
{: #wks_projtypesysmod}

You might need to make modifications while you train an annotator, based on the performance statistics. But, generally, you want the type system to be as close to final as possible before you begin large-scale annotation tasks. If you change the type system after human annotators began their work, they must revisit the documents that they annotated. They must assess the applicability of the type system changes.

### About this task

This process propagates the current type system, Ground Truth Editor keyboard shortcuts, and color settings to all document sets in a task.

### Procedure

An application process manager can modify the type system without losing the work that was done by human annotators as follows:

1. Change the type system. For example, you can add or remove entity types or relation types.
1. Decide whether you want to propagate the changes to existing human annotation tasks.
1. On the **Human Annotation** page, open each task that you want to update and click **Apply Type System Updates**.

    If you removed entity types or relation types from the type system, all occurrences of those types are highlighted in gray in the documents. These invalid types are ignored by the machine-learning annotator. They do not prevent you from submitting and approving document sets.

1. Provide details to the human annotators about what changed in the type system.
1. Ask human annotators to update their documents to reflect the changes in the type system. For example, if you added new entity types or relation types, they must review their documents and annotate them appropriately.

    > **Note:** If the task contains completed documents, human annotators cannot alter those documents to assess type system changes until they are back in an editable state. To become editable, ask human annotators to submit the document sets so that you can reject them.

**Related concepts**:

[Type systems](/docs/services/knowledge-studio/typesystem.html#wks_typesystem)

## Document set management
{: #wks_mamanagedata}

Use the right sets of data to test and train the annotator component at the right time.

The documents that you add to the system must be allocated to the following system-level data sets when you create a machine-learning annotator:

- **Training set**

    A set of documents that have been annotated through pre-annotation or by human annotators that is used to train the annotator component. The goal of the training set is to teach the machine-learning model about correct annotations, which includes teaching the model through text that was not annotated.

- **Test set**

    A set of annotated documents that is used to test the trained annotator component. After you run a test on the test set, perform a detailed diagnostic-purposed error analysis of the results. Close analysis helps you find weaknesses in the current model that can be addressed.

- **Blind set**

    A set of annotated documents that is set aside and used to test the system periodically after several iterations of testing and improvement have occurred. To prevent accuracy from being tainted (for example, by making changes based only on annotations in known documents), blind data should be data that has not previously been viewed by users involved with creating the annotator component. Reported results should come only from tests that are run on blind data. After you run a test on the blind set, look at only the most high-level scores, such as the overall mention and relation F1 scores. You don't want to learn too many details about the performance or it might influence the improvements that you choose to make to the model.

The goal of {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} is to enable large teams to work together to build models. As such, it assumes that models are being produced by a team that includes a group of human annotators and a separate person or group of people that builds and tests the model, and makes improvements to it. Due to this assumption, the application is configured to push an equally proportioned grouping of documents from a single document set into the test, train, and blind sets. However, if your team is not segregated - if the people doing human annotation are also reviewing model test results in detail, for example - then you might need to change the allocation of documents into these sets to more explicitly separate the documents that are being used in each one.

### Why do I need a blind set?

Because you use test data to assess accuracy in detail, you get to know the documents and their features after a while. For example, you start to know which entity types, relation types, and text types in the documents are best understood by the machine learning model, and which are not. This information is important because it helps you focus on making the right improvements - refining the type system, supplementing the training data to fill gaps, or adding dictionaries, for example. As the test documents get used iteratively to improve the model, they can start to influence the model training indirectly. That's why the "blind" set of documents is so important.

### How do I control which documents are allocated to a set?

When you create a machine-learning annotator, you must specify the ratio of documents from the set to allocate to the train, test, or blind sets. {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} automatically applies a ratio of 70/23/7 to the document sets that you use to build a machine-learning annotator. You can change these values.

- To add a set that was annotated by humans to the training set, specify a 100/0/0 breakdown ratio.
- After training with a set, you can use it for testing. To use a document set for testing only, specify a 0/100/0 breakdown ration.
- Only add a document set that has never been used for training or testing to the blind set. To do so, specify a 0/0/100 breakdown ratio for the document set.

Plan to stop using a blind set after a few iterations. The more you use a blind set, the less "blind" it becomes. The same goes for your test data. Rather than discard the sets, you can migrate them to serve a new purpose. Follow this migration flow:

```
blind --> test --> train
```
{: screen}

As the sets migrate, you can add new, unseen document sets as blind data, and as test data. But, be sure to retain a method for evaluating accuracy across model versions. One way to establish a baseline is to run an earlier version of the model on the new document sets. The results of this run give you a basis of comparison with runs of newer models on those same sets.
