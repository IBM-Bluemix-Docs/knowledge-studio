---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-16"

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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.IBM}} Marketplace. To see the documentation for the new version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/docs/services/watson-knowledge-studio/accessibility.html){: new_window}.
{: tip}

# Backing up and restoring data
{: #backup-restore}

If you need to backup and restore a workspace for {{site.data.keyword.knowledgestudioshort}}, perform these tasks. Also, if you need to perform a manual data migration from one {{site.data.keyword.knowledgestudioshort}} instance to another, such as when migrating from an instance on {{site.data.keyword.IBM_notm}} Marketplace to an instance on {{site.data.keyword.cloud_notm}}, perform these tasks.
{: shortdesc}

_Manual data migration_ is the process of backing up your data from one instance and restoring it on another instance.

**Note**: {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}} uses the term _workspace_, while {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace uses the term _project_. The functionality is the same. Only the terminology is different.

To back up and restore your data complete the following steps:

1. [Understand which data can be backed up](#data)
1. [Prepare for backup](#prepare)
1. [Export artifacts from the current instance](#export)
1. [Recreate workspaces on the new instance](#recreateproj)
1. [Restore the workspace data](#restoredata)
1. [Restore the machine learning models](#restoremodels)
1. [Restore any incomplete annotation tasks](#restoretasks)

## Data that can be backed up
{: #data}

The following artifacts can be backed up and migrated manually:

- Editable dictionaries
- Type system
- Approved ground truth document sets

The following types of artifacts cannot be backed up and migrated manually:

- In-progress human annotation documents
- Annotation tasks
- Machine learning models and snapshots
- Read-only dictionaries

## Preparing for backup
{: #prepare}

To prepare for backing up and restoring your data, complete the following steps:

1. Complete any work that is in progress in your workspace.

    - > **Important:** Finish any in-progress annotation tasks. Only documents that have been annotated, adjudicated, and approved and promoted to ground truth can be backed up. If you do not finish the annotation work, you will lose any annotation effort that is in progress, but not completely done.

    - If you created annotation tasks to track work that you want to do, but none of the annotation work has begun and will not take place until after the workspace is restored, then make a list of the outstanding annotation tasks. Be sure to note the document sets that you imported, but that have not been added to the ground truth yet. Also, make a note of who you assigned to annotate each document set. You will need to reimport these document sets and recreate the annotation tasks after the workspace is restored.

1. Understand tokenizer use.

    Workspaces use the machine learning-based tokenizer by default. If you are using a dictionary-based tokenizer and have a specific need to continue doing so, you can configure the workspace to use the dictionary-based tokenizer when you restore it. For more information, see [Tokenizers](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer).

1. Manage machine learning model resources.

    Your machine learning model, its versions, and snapshot data cannot be migrated. The resources (except read-only dictionaries) that you used to train those artifacts can be migrated. Therefore, after the migration, you can recreate the machine learning model. The model that will be produced will perform the same as the models you generated prior to the migration because the resources that are used for training will be the same.

    **ATTENTION**: If you have a model that is already deployed and you plan to delete the workspace after you back it up, withdraw the model from deployment before you delete the workspace. You can rebuild and redeploy the model after you restore the workspace from the backup.

    **Be aware that if you fail to withdraw the model from deployment before you delete the workspace, the result is an _orphaned_ deployed model that cannot be undeployed. Orphaned deployed models will continue to generate charges on your monthly bills.**

1. Manage read-only dictionary information.

    Read-only dictionaries cannot be migrated. Find out where the read-only dictionary was imported from, so you can reimport it to your workspace after the migration.

1. Make a list of current user roles.

    **NOTE**: This step is optional. It is typically performed when a workspace is migrated across instances and the new workspace must be identical to the original workspace. If you want to migrate only the workspace data into a new workspace, you can skip this step.

    If you are migrating workspaces across different instances, consider making a list of users and their roles for the instance that you are backing up. Someone with the Admin role can print the list from the User Account Management page. After the workspaces are recreated on the new instance, someone with the Admin role must add the users and assign their roles.

    See [Assembling a team](/docs/services/watson-knowledge-studio/team.html) for more information about the roles.

1. Make note of workspace information.

    While you still have access to the current instance, for each workspace that you want to migrate, make a note of the following information:
    - Workspace name
    - Workspace description
    - Workspace owner
    - Language
    - If you have any incomplete annotation tasks, because they can't be backed up or migrated, note the human annotators who are assigned to incomplete tasks in the workspace. Also note the annotation task details, such as the task name, due date, and which document sets are assigned to which users.

## Exporting artifacts
{: #export}

For each workspace that you want to migrate, export the following artifacts. Store them in a secure location from which you will be able to import them into the new instance later.

- Type system
- Dictionaries

  **Note**: Only editable dictionaries will be exported. You cannot export read-only dictionaries.

- Documents

  See [Importing resources from another workspace](/docs/services/watson-knowledge-studio/exportimport.html) for information about how to export these artifacts so that they can be imported into a new workspace.

## Recreating workspaces
{: #recreateproj}

**NOTE**: In this step, the only setting that must match the setting of the original (exported) workspace is the language. The rest of the settings can differ from the settings of the original workspace.

Recreate each workspace by copying the following information from the previous instance to the new one:

- Workspace name
- Workspace description
- Language of documents (this setting must match the setting in the original workspace)
- If you previously used a dictionary-based tokenizer in the workspace, and have a valid need to continue using it, you must specify that you want to use the dictionary-based tokenizer instead of the default tokenizer at the time that you create the workspace. For more information about the options, see [Tokenizers](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer).

  To use a dictionary-based tokenizer, expand the Advanced Options section of the Create Workspace window (in {{site.data.keyword.IBM_notm}} Marketplace, the Create Workspace window) and change the tokenizer setting.

## Restoring workspace data
{: #restoredata}

After recreating the workspaces, import the previously exported artifacts:

1. Import the type system from the previously created type system backup.
   For details, see [Importing resources from another workspace](/docs/services/watson-knowledge-studio/exportimport.html).

  **Note**: You must import the type system before you can import any other artifacts that you are moving from the backed up workspace.

1. Import the dictionaries from the previously created dictionary backup.
   For details, see [Importing resources from another workspace](/docs/services/watson-knowledge-studio/exportimport.html).

  If you used any read-only dictionaries in the previous version of the workspace, reimport them into this workspace from their original source.

  **Note**: When you add dictionaries, the dictionary pre-annotator is automatically created. You associate the dictionary with an entity type at the time when you run the pre-annotator.

1. Import the documents that you exported from the previous version of the workspace into this version of the workspace.
   For details, see [Importing resources from another workspace](/docs/services/watson-knowledge-studio/exportimport.html).

## Restoring machine learning models
{: #restoremodels}

At this point, all the artifacts that were used to train the model in the previous (backed up) version of the workspace are now available in this new instance. To redeploy a machine learning model that you deployed in the previous instance, complete the following steps:

1. Train the machine-learning annotator component to produce a model. For details, see [Creating a machine-learning annotator component](/docs/services/watson-knowledge-studio/train-ml.html).

  **Note**: Do not run any pre-annotators on annotated documents that you migrated to this workspace because they will lose any annotations in them that were added by human annotators.

1. After creating the model, deploy it again. For details, see [Using the machine-learning model](/docs/services/watson-knowledge-studio/publish-ml.html).

## Restoring incomplete annotation tasks
{: #restoretasks}

If you had any annotation tasks that were created, but not completed in the previous workspace, complete the following steps to recreate the incomplete annotation tasks:

1. Import any documents that have not been annotated yet, but that you want to add to the ground truth to continue to improve the model.
1. From the newly imported and unannotated documents, create document sets for annotation. These sets are now called _annotation sets_. For details, see [Creating and assigning annotation sets](/docs/services/watson-knowledge-studio/document-for-annotation.html).
1. Recreate the annotation tasks. Give the task the same name, an appropriate due date, and assign annotation sets to the appropriate human annotators.
