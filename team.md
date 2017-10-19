---

copyright:
  years: 2015, 2017
lastupdated: "2017-10-19"

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

# Assembling a team
{: #team}

The creation of an annotator component requires input from subject matter experts, project managers, and users who can understand and interpret statistical models. A user account must be created for each user who needs to log in to {{site.data.keyword.watson}}&trade; {{site.data.keyword.knowledgestudioshort}}.
{: shortdesc}

## Before you begin

You should have already performed these tasks:

- Registered with [myibm.ibm.com](https://myibm.ibm.com/), and created an {{site.data.keyword.IBM_notm}} ID.
- From [{{site.data.keyword.IBM_notm}} Marketplace ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/watsonknowledge){: new_window}, sign up for a plan for {{site.data.keyword.knowledgestudiofull}} that allows for more than one user.

    An instance of {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} is created for you to use. You are the subscription owner. Your {{site.data.keyword.IBM_notm}} ID is automatically given administrative access to the instance. As an administrator, you can then invite others.

## About this task

Invite people to fill the following roles.

> **Important:** If you have a free plan subscription, you cannot invite others to access your instance of {{site.data.keyword.knowledgestudioshort}}. Instead, you are added to the instance as an administrator. In the administrator role, you can perform many functions that would typically be performed by different people who are invited and assigned to different roles. You can test out how easy it is for experts from different areas of a domain to work together to build a machine-learning or rules-based model.

- **Human annotator**

    The human annotator is someone, typically a subject matter expert, who reviews domain documents to identify entities and relationships of interest to the domain. This user interacts with the application in a limited way; she uses the Ground Truth Editor to annotate a set of documents that have been assigned to her.

- **Project manager**

    The project manager is someone who helps to facilitate the creation of annotator components by performing such tasks as creating project artifacts, and training, creating, and deploying models. For projects that build machine-learning annotators, they also manage the document annotation process by assigning document review tasks to human annotators, adjudicating annotation conflicts, and approving documents to add to the ground truth.

## Adding users

To add users to a {{site.data.keyword.knowledgestudioshort}} instance:

1. Log in to the My {{site.data.keyword.IBM_notm}} Products and Services page with your {{site.data.keyword.IBM_notm}} ID: [https://myibm.ibm.com/products-services/ ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://myibm.ibm.com/products-services/){: new_window}
1. Click **Manage** on the {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} offering tile.
1. Click **Manage users**. To invite a user, add the {{site.data.keyword.IBM_notm}} ID or email address of the person that you want to invite. If you want the user to be authorized to invite more users, select the **Administrator** check box. Keep in mind that most subscriptions have a user limit.

    > **Note:** If you select the **Administrator** check box, that action gives the user administrative access to the subscription, not to the {{site.data.keyword.knowledgestudioshort}} application. An administrator can invite or disinvite users to the {{site.data.keyword.knowledgestudioshort}} instance.

1. Click **Submit**.

    Repeat this process to invite more people.

    Invitees receive an email, which provides information about how to complete their registration.

    > **Note:** Everyone who is invited, whether they are a subscription administrator or not, is automatically assigned the HUMANANNOTATOR role within {{site.data.keyword.knowledgestudioshort}}. Only the subscription owner is assigned to the ADMIN role within {{site.data.keyword.knowledgestudioshort}}. The {{site.data.keyword.knowledgestudioshort}} ADMIN must explicitly upgrade the user role within {{site.data.keyword.knowledgestudioshort}} to grant additional privileges.

## Upgrading user roles

Users must be assigned the roles described below to be able to perform the respective tasks. A user's role can be upgraded from a lower role to a higher role.

> **Attention: Downgrading from a higher role to a lower role is not permitted.**

To upgrade roles for {{site.data.keyword.knowledgestudioshort}} users:

1. Log in to {{site.data.keyword.knowledgestudioshort}} with your administrator ID.
1. Click the **Settings** icon ![the Settings icon](images/settings.png) in the top right corner to open the User Account Management page. The page lists all the user IDs that are registered as {{site.data.keyword.knowledgestudioshort}} users.
1. Find the user's name you want to change and click the **Modify account setting** icon ![the "Modify account setting" icon](images/action.png).

    {{site.data.keyword.knowledgestudioshort}} has the following roles, which are listed from the highest level to the lowest level of privileges:
    - **ADMIN**

        Users in this role can:
        - Manage a subscription, such as add features, storage, and more users
        - Give users access to a subscription from the User Account Management page
        - Create and manage all projects in their subscription
        - Assign people to the project manager or human annotator roles for all projects

    - **PROJECTMANAGER**

        Users with this role can:
        - Manage projects to which they are added
        - Assign human annotators to a project

        Users with this role cannot:
        - Create projects
        - Manage user access and roles from the User Account Management page

    - **HUMANANNOTATOR**

        Users with this role can annotate documents that are in projects where they are assigned the human annotator role, and in a document set that is associated with aannotation tasks that are assigned to them.

        > **Important:** You must create a project, associate this user with a document set, and assign an annotation task to this user before the user will be able to see any projects listed in the {{site.data.keyword.knowledgestudioshort}} application. Set up the project as soon as possible after people you invited register, so that they will see your project when they first access the application. You might want to notify users after you set up the project to let them know that they can start annotating documents.

1. Click the role of the user and choose the role you want to upgrade that user to.
1. Optional: When you finish administering users in {{site.data.keyword.knowledgestudioshort}}, exit the session by closing the web browser. The {{site.data.keyword.knowledgestudioshort}} user interface does not provide an action for explicitly logging out.

## What to do next

Later, if you want to remove users, log in to the My {{site.data.keyword.IBM_notm}} Products and Services page, and from the Manage authorizations panel, click the right arrow next to the name of the user that you want to remove. Select **Remove user**, and then click **Save changes**.

> **Warning:** If users are assigned documents to annotate and you delete their accounts, their annotations are affected. If annotations made by deleted users were not promoted to ground truth, those annotations are deleted.

### Related tasks

[Creating and assigning annotation sets](/docs/services/knowledge-studio/documents-for-annotation.html#wks_projdocsets)
