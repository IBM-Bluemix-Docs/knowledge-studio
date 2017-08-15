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

# Upgrading your subscription
{: #upgrade}

Understand how to move from a free plan to a paid plan or change your subscription plan.
{: shortdesc}

To upgrade the level of your service, go to the [{{site.data.keyword.IBM_notm}} Marketplace {{site.data.keyword.knowledgestudiofull}}  ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/marketplace/cloud/supervised-machine-learning/){: new_window} page.

## December 2016 release
{: #upgrade_dec_ovw}

With the December release, the {{site.data.keyword.watson}}&trade; {{site.data.keyword.knowledgestudioshort}} service is being re-architected. The benefit of this change is that it will improve the performance and stability of the application. However, it will impact your current instance.

### Paid subscriptions

For paid subscriptions, {{site.data.keyword.IBM_notm}} will provision a new instance in the new environment. {{site.data.keyword.IBM_notm}} will migrate your data for you, unless you choose to migrate your own data. If you would like to migrate your own data, let {{site.data.keyword.IBM_notm}} support know by sending mail to `wkssupp@us.ibm.com`.

Users who had access to the previous subscription will be added to the new tenant with the human annotator role. If you choose to migrate your own data, you must recreate the projects that you want to continue using in the new instance.

### Trial subscriptions

Data from trial subscriptions will not be migrated. If you have a trial subscription and want to continue using data from it in the upgraded environment, then you must migrate the data yourself before the trial expires.

### What data will be migrated

The following artifacts can be moved from the previous instance to the new one:

- Editable dictionaries
- Type system
- Approved ground truth document sets

The following types of artifacts cannot be migrated:

- In-progress human annotation documents
- Annotation tasks
- Machine learning models and snapshots
- Read-only dictionaries

## Preparing for migration
{: #wks_migrate_dec2016}

Whether you or {{site.data.keyword.IBM_notm}} will migrate your data to the December 2016 version of the product software, there are steps you must take to prepare for the migration.

### Procedure

To prepare for the migration of your data, complete the following steps:

1. Complete any work that is in progress in your projects.

    - > **Important:** Finish any in-progress annotation tasks. Only documents that have been annotated, adjudicated, and approved and promoted to ground truth can be moved to the new instance. If you do not finish the annotation work, you will lose any annotation effort that is underway, but not completely done.

    - > **Important:** If you have a model that is currently deployed for use in the {{site.data.keyword.alchemylanguageshort}} service, then you must withdraw the model from deployment before the upgrade. After the upgrade is completed, you can recreate the model and redeploy it. You must perform this task before the upgrade because you will not be able to manage any existing models, which includes withdrawing them from deployment, after the migration.

    - If you created annotation tasks to track work that you want to do, but none of the annotation work has begun and will not take place until after the migration, then make a list of the outstanding annotation tasks. Be sure to note the document sets that you imported, but that have not been added to the ground truth yet. Also, make a note of who you assigned to annotate each document set. You will need to re-import these document sets and recreate the annotation tasks after the migration.

1. Understand the tokenizer change.

    With the December 2016 release, new projects use the machine learning-based tokenizer by default. If you are using a dictionary-based tokenizer and have a specific need to continue doing so, you can configure the project to use the dictionary-based tokenizer when you recreate it. If {{site.data.keyword.IBM_notm}} is migrating your data for you and you want to continue using a dictionary-based tokenizer, then let the {{site.data.keyword.IBM_notm}} support team know before your instance is migrated by sending an email to `wkssupp@us.ibm.com`. See [Tokenizers](/docs/services/knowledge-studio/create-project.html#wks_tokenizer) for more information.

1. Manage machine-learning annotator resources.

    Your machine-learning model, its versions, and snapshot data cannot be migrated. The resources (except read-only dictionaries) that you used to train them can be migrated. Therefore, after the migration, you can recreate the machine-learning annotator component. The model that will be produced should perform the same as models you generated before since the resources used for training will be the same.

    If you have a machine-learning model that has been trained and is performing well now, hold off deploying it until after the upgrade. And if you have a model that is already deployed, withdraw it from deployment before the upgrade. You can redeploy it afterward.

1. Manage read-only dictionary information.

    Read-only dictionaries that you are using cannot be migrated. Find out where the read-only dictionary was imported from, so you can re-import it to your project after the migration.

1. Get a list of current user roles.

    The user roles are changing with this upgrade. Consider getting a list of the users who have access to your instance, and their current role assignments. (Someone with super_user level access can print the current list from the User Account Management page.) If {{site.data.keyword.IBM_notm}} is migrating your data, these users will be re-added to the new instance after the upgrade, and will be assigned to the new roles. If you are migrating your data yourself, you must re-add the users and map them to the appropriate roles. The roles are changing as follows:
    - Super user -&gt; Administrator
    - Master Admin -&gt; Project Manager
    - Human annotator -&gt; Human Annotator

    See [Assembling a team](/docs/services/knowledge-studio/team.html) for more information about the roles.

## Migrating data yourself
{: #wks_migrate_self}

If you have a paid subscription and want to migrate your data yourself, or have a trial subscription, complete this procedure to migrate your own data. If you have a paid subscription and do not want to migrate your own data, you can skip this procedure and let the {{site.data.keyword.IBM_notm}} Support team migrate the data for you.

### Before you begin

Before you lose access to your current instance, complete these steps:

1. For each project that you want to migrate, make a note of the following information:

    - Project name
    - Project description
    - Project owner
    - Language
    - Any human annotators who are assigned to incomplete annotation tasks in the project, and the annotation task details, such as the task name, due date, and which document sets are assigned to which users.

1. For each project that you want to migrate, export the following artifacts.

    Store them in a secure location from which you will be able to import them into the new instance later:
    - Type system
    - Dictionaries

        > **Note:** Only editable dictionaries will be exported. You cannot export read-only dictionaries.

    - Documents

    See [Importing resources from another project](/docs/services/knowledge-studio/exportimport.html) for information about how to export these artifacts so that they can be imported into a new project.

### About this task

If you have a paid subscription to the service and want to migrate your own data, then the {{site.data.keyword.IBM_notm}} team will provision a new instance of {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} for you in the post-December 2016 release environment. When you are contacted by {{site.data.keyword.IBM_notm}} with the new instance information, you can perform the following steps to migrate your data.

If you have a trial subscription, your instance will not be migrated. You must sign up for a new subscription in the new environment, and recreate the projects using artifacts that you exported from your original trial instance.

### Procedure

To migrate your data yourself, complete the following steps:

1. From the new instance, reassign users to the appropriate roles.

    If you had a paid subscription to the service before the December 2016 release, everyone who had access to the previous instance was given access to the new instance, but in the human annotator role. Only the instance owner is added in the Administrator role. You, as the Administrator, must reassign users to the appropriate roles. The role names changed with the December 2016 release as follows:
    - Super user -&gt; Administrator
    - Master Admin -&gt; Project Manager
    - Human annotator -&gt; Human Annotator

    See [Assembling a team](/docs/services/knowledge-studio/team.html) for more information about the roles.

1. Recreate your projects in the new instance.

    Recreate each project. Copy the following information from the previous instance to the new one:
    - Project name
    - Project description
    - Language of documents (this field name changed from Language in the previous version)
    - For anyone who is not an Administrator, but must be able to manage the annotation process or train models, you must add them to the project as a project manager. This role is new with the December 2016 release. Project managers cannot create a project, but can perform all other administrative tasks within a project after they are added to it. Typically, anyone who was a creator of a project in the previous instance and is not an Administrator should be added as a project manager in this instance.

        To add project managers, expand the **Advanced Options** section of the Create Project window, and select users that you want to add as project managers from the list. Only people that you added to the instance in the project manager role in the previous step are displayed as options.

        > **Note:** You can skip this step if the person in the Administrator role will perform all administrative tasks for the project.

    - If you used a dictionary-based tokenizer in this project previously, and have a valid need to continue using it, you must specify that you want to use the dictionary-based tokenizer instead of the default tokenizer at the time that you create the project. See [Tokenizers](/docs/services/knowledge-studio/create-project.html#wks_tokenizer) for more details.

        To do so, expand the **Advanced Options** section of the Create Project window and change the tokenizer setting.

1. Import the type system that you exported from the previous version of the project into this version of the project

    See [Importing resources from another project](/docs/services/knowledge-studio/exportimport.html) for details.

    > **Note:** You must import the type system before you can import any other artifacts that you are moving from the previous version of the project to this one.

1. Import the dictionaries that you exported from the previous version of the project into this version of the project.

    See [Importing resources from another project](/docs/services/knowledge-studio/exportimport.html) for details.

    If you used any read-only dictionaries in the previous version of the project, re-import them into this project.

    > **Note:** When you add dictionaries, the dictionary pre-annotator is automatically created. With the December 2016 release, instead of associating the dictionary with an entity type at the time that the dictionary is created or imported, you perform the type-mapping step when you run the pre-annotator.

1. Import the documents that you exported from the previous version of the project into this version of the project.

    See [Importing resources from another project](/docs/services/knowledge-studio/exportimport.html) for details.

1. To redeploy a machine-learning model that you deployed before, you must retrain the annotator.

    At this point, all of the artifacts that were used to train the annotator in the previous version of the project are now available in this version of the project. You can run the machine-learning annotator component to produce a model. See [Creating a machine-learning annotator component](/docs/services/knowledge-studio/train-ml.html#wks_madocsets) for details.

    > **Note:** Do not run any pre-annotators on annotated documents that you migrated to this project because they will lose any annotations in them that were added by human annotators.

    After creating the model, deploy it again. See [Using the machine-learning model](/docs/services/knowledge-studio/publish-ml.html) for details.

1. If you had any annotation tasks that were created, but not started in the previous version, you can recreate them now. Complete these steps to do so:

    1. Import any documents that have not been annotated yet, but that you want to add to the ground truth to continue to improve the model.
    1. From the newly imported and un-annotated documents, create document sets for annotation. These sets are now called *annotation sets*. See [Creating and assigning annotation sets](/docs/services/knowledge-studio/document-for-annotation.html#wks_projdocsets) for more details.
    1. Recreate the annotation tasks. Give the task the same name, an appropriate due date, and assign annotation sets to the appropriate human annotators.

## Reviewing projects migrated by IBM
{: #wks_migrate_ibm}

After the {{site.data.keyword.IBM_notm}} Support team migrates your data, you can log into the new instance and use your projects. This procedure describes some additional steps you must take to return the projects to their previous state.

### Procedure

To review projects that were migrated by {{site.data.keyword.IBM_notm}}, complete the following steps:

1. Check the users associated with your projects.

    People with the Project Manager role cannot create projects. Therefore, if a user was migrated from the Master Administrator role to the Project Manager role, but should also be able to create projects, then consider changing their role to Administrator instead. Keep in mind that this assignment also gives them the ability to manage the subscription (add features, increase the number of users, and so on).

1. Re-import any read-only dictionaries that you want to use.
1. Recreate any annotation tasks that were not completed in the previous version. To do so:

    1. Re-import any document sets that had not been annotated in the previous version. Create annotation sets from the imported documents. See [Creating and assigning annotation sets](/docs/services/knowledge-studio/document-for-annotation.html#wks_projdocsets) for more details.
    1. Recreate the annotation tasks. Copy the annotation name, assign an appropriate due date, and assign the annotation sets to the appropriate human annotators.

1. Create a machine-learning annotator component and run training to re-produce the machine-learning model.

