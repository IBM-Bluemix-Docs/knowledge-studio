---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-03"

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

# Troubleshooting and support
{: #troubleshooting}

To isolate and resolve problems with your {{site.data.keyword.IBM_notm}} products, you can use the troubleshooting and support information. This information contains instructions for using the problem-determination resources that are provided with your {{site.data.keyword.IBM_notm}} products, including {{site.data.keyword.knowledgestudiofull}}.
{: shortdesc}

## Techniques for troubleshooting problems
{: #ts_overview}

*Troubleshooting* is a systematic approach to solving a problem. The goal of troubleshooting is to determine why something does not work as expected and how to resolve the problem. Certain common techniques can help with the task of troubleshooting.

The first step in the troubleshooting process is to describe the problem completely. Problem descriptions help you and the {{site.data.keyword.IBM_notm}} technical-support representative know where to start to find the cause of the problem. This step includes asking yourself basic questions:

- What are the symptoms of the problem?
- Where does the problem occur?
- When does the problem occur?
- Under which conditions does the problem occur?
- Can the problem be reproduced?

The answers to these questions typically lead to a good description of the problem, which can then lead you to a problem resolution.

### What are the symptoms of the problem?

When starting to describe a problem, the most obvious question is "What is the problem?" This question might seem straightforward; however, you can break it down into several more-focused questions that create a more descriptive picture of the problem. These questions can include:

- Who, or what, is reporting the problem?
- What are the error codes and messages?
- How does the system fail? For example, is it a loop, hang, crash, performance degradation, or incorrect result?

### Where does the problem occur?

Determining where the problem originates is not always easy, but it is one of the most important steps in resolving a problem. Many layers of technology can exist between the reporting and failing components. Networks, disks, and drivers are only a few of the components to consider when you are investigating problems.

The following questions help you to focus on where the problem occurs to isolate the problem layer:

- Is the problem specific to one platform or operating system, or is it common across multiple platforms or operating systems?
- Is the current environment and configuration supported?
- Do all users have the problem?
- (For multi-site installations.) Do all sites have the problem?

If one layer reports the problem, the problem does not necessarily originate in that layer. Part of identifying where a problem originates is understanding the environment in which it exists. Take some time to completely describe the problem environment, including the operating system and version, all corresponding software and versions, and hardware information. Confirm that you are running within an environment that is a supported configuration; many problems can be traced back to incompatible levels of software that are not intended to run together or have not been fully tested together.

### When does the problem occur?

Develop a detailed timeline of events leading up to a failure, especially for those cases that are one-time occurrences. You can most easily develop a timeline by working backward: Start at the time an error was reported (as precisely as possible, even down to the millisecond), and work backward through the available logs and information. Typically, you need to look only as far as the first suspicious event that you find in a diagnostic log.

To develop a detailed timeline of events, answer these questions:

- Does the problem happen only at a certain time of day or night?
- How often does the problem happen?
- What sequence of events leads up to the time that the problem is reported?
- Does the problem happen after an environment change, such as upgrading or installing software or hardware?

Responding to these types of questions can give you a frame of reference in which to investigate the problem.

### Under which conditions does the problem occur?

Knowing which systems and applications are running at the time that a problem occurs is an important part of troubleshooting. These questions about your environment can help you to identify the root cause of the problem:

- Does the problem always occur when the same task is being performed?
- Does a certain sequence of events need to happen for the problem to occur?
- Do any other applications fail at the same time?

Answering these types of questions can help you explain the environment in which the problem occurs and correlate any dependencies. Remember that just because multiple problems might have occurred around the same time, the problems are not necessarily related.

### Can the problem be reproduced?

From a troubleshooting standpoint, the ideal problem is one that can be reproduced. Typically, when a problem can be reproduced you have a larger set of tools or procedures at your disposal to help you investigate. Consequently, problems that you can reproduce are often easier to debug and solve.

However, problems that you can reproduce can have a disadvantage: If the problem is of significant business impact, you do not want it to recur. If possible, re-create the problem in a test or development environment, which typically offers you more flexibility and control during your investigation.

- Can the problem be re-created on a test system?
- Are multiple users or applications encountering the same type of problem?
- Can the problem be re-created by running a single command, a set of commands, or a particular application?

## AlchemyLanguage model issues
{: #wks_ts_deployed_model_deleted}

### Problem

You cannot deploy an AlchemyLanguage model or the deployment succeeded but the model is not available for use.

### Symptoms

- You deployed a model, but the status shows that an error occurred.
- You deployed a model and the status indicated that the model was available, but you cannot use it.
- The model was deployed successfully and worked before, but now it does not work.

### Causes

The following events can cause problems with deployed models:

- If you mistype the {{site.data.keyword.alchemyapishort}} key when you add the key to the `apikey` parameter of the REST API call, then the call will fail. The same is true for the model ID. It is best to copy and paste the model ID and API key to avoid typing errors.
- If you provide an {{site.data.keyword.alchemyapishort}} key that is invalid or is not authorized to deploy a custom model, then the deployment process will indicate that the model was successfully deployed, but you will not be able to use it.
- If, while using {{site.data.keyword.alchemylanguageshort}} in {{site.data.keyword.Bluemix}}, you delete all of the service instances that are associated with an {{site.data.keyword.alchemyapishort}} key in {{site.data.keyword.Bluemix_notm}}, then any deployed models that reference that key will be removed from the service. {{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}} periodically checks whether registered models are associated with a valid key, and any models that are not, are deleted. If your model was deployed against a key that gets deleted, the status of the model will change to `error`.

### Resolving the problem

1. Check the status of the deployment.

    Log in as a {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} administrator. Open the **Annotator Component** page, and click **Details**. On the Versions tab, click **Status** to check the status of the model that you deployed.

1. If the deployment status of the model is `error` or the status is `available`, but the model does not work when you try to use it, then withdraw the model from deployment by clicking **Undeploy**.
1. Redeploy the model.

    Use only a valid {{site.data.keyword.alchemyapishort}} key that has authorization to deploy models, and copy and paste the model ID and API key when you add them as parameters to the API call.

**Related tasks**:

[Deploying a machine-learning annotator to {{site.data.keyword.IBM_notm}} {{site.data.keyword.alchemylanguageshort}}](/docs/services/knowledge-studio/publish-ml.html#wks_mabluemix)

### Problem

You cannot pre-annotate documents with the AlchemyLanguage pre-annotator.

### Symptom

When you try to pre-annotate documents with the AlchemyLanguage pre-annotator, you see the following error message:

`PREANNOTATE: The process failed. An AlchemyAPI error occurred: Reach API limit`

### Cause

There is a daily API call limit for the service.

### Resolving the problem

Wait 24 hours, and then run the pre-annotator again.

## Can't create a free account
{: #wks_ts_free}

### Problem

You try to create a free account and see the error message, `Error 331: We are unable to process your request. Please try again later or contact the {{site.data.keyword.IBM_notm}} Helpdesk.`

### Causes

{{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} does not permit more than one free account per organization.

### Resolving the problem

Create an account that is not included in the organization.

If you need to use your current account for the free trial and your user account is associated with a paid account, you can submit a support ticket. For more information, see [Contacting {{site.data.keyword.IBM_notm}} Support](/docs/services/knowledge-studio/troubleshooting.html#ts_contactingibmsupport).

If you need to use your current account for the free trial and your user account isn't associated with a paid account, post your issue to [{{site.data.keyword.IBM_notm}} developerWorks Answers](https://developer.ibm.com/answers/topics/wks/), making sure to tag the question, **WKS**.

## Cannot access the application
{: #wks_ts_access}

Find out how to grant users access to {{site.data.keyword.watson}}&trade; {{site.data.keyword.knowledgestudioshort}}, and address common access issues.

You must have {{site.data.keyword.IBM_notm}} user registration credentials to request an instance of {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}}.

### Administrator

Each {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} instance has an administrator role associated with it. The person who originally signs up to use the application is given the administrator role automatically. The administrator can invite other people.

For information about how to invite people to use your instance of the application, see [Assembling the team](/docs/services/knowledge-studio/team.html).

### Human annotator

If you have been invited to someone's instance of {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} to serve as a human annotator, you likely received an email invitation. First, you must register with {{site.data.keyword.IBM_notm}} if you do not have {{site.data.keyword.IBM_notm}} registration credentials already. Once you register with {{site.data.keyword.IBM_notm}} and accept the invitation, you are given access to the instance. However, after you are given access and before you can start to annotate documents, the administrator or a project manager of the instance must add you to a project and assign an annotation task to you. It is not until after you have been assigned a task that you can perform any actions in the {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} instance. To annotate documents, use the Ground Truth Editor. Use a Google Chrome browser for the best performance.

For help using the Ground Truth Editor, see the [User Guide: Ground Truth Editor](/docs/services/knowledge-studio/user-guide.html).

## Experimental services: What does *experimental* mean?
{: #experimental}

For information about experimental services, see the [{{site.data.keyword.Bluemix_notm}} documentation](/docs/services/index.html#experimental_services). For the full details of experimental services, see the latest version of the [{{site.data.keyword.IBM_notm}} {{site.data.keyword.Bluemix_notm}} Service Description ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/software/sla/sladb.nsf/searchsaas/?searchview&searchorder=4&searchmax=0&query=IBM+Bluemix+Service+Description){: new_window}.

## Storage space issues
{: #storage}

Depending on your subscription plan, you might hit the storage limit specified for your plan and be prevented from performing tasks that you want to complete.

### Symptoms

You might see a message about having exceeded the allowed storage space when you attempt to perform one of these tasks:

- Upload documents or dictionaries
- Deploy a model or version a model
- Run a pre-annotator on documents

### Causes

The storage limit has been met or would be exceeded if the action were to proceed.

### Resolving the problem

The largest consumers of storage space are machine-learning and rule-based models. To free up space, you can take the following actions:

- Delete snapshot versions of any models that you do not expect to need to revert to.
- Delete any models that you do not need.
- If your models are too important to delete, consider upgrading your plan to one that provides a larger allotment of storage space.

After removing models or model versions, wait an hour before you retry the action that resulted in the error message. It can take up to an hour for the storage space that you freed up to be available for use.

## Contacting IBM Support
{: #ts_contactingibmsupport}

{{site.data.keyword.IBM_notm}} Support provides assistance with product defects, answers FAQs, and helps users resolve problems with the product.

### Before you begin

First, see if a solution is documented for the problem you are having. Search {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} on the [{{site.data.keyword.IBM_notm}} Support Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/home/entry/portal){: new_window}. On the search results page, click the **Support** tab to see results from tech notes, {{site.data.keyword.IBM_notm}} Redbooks, and documentation. Click the **For developers** tab to see results from the {{site.data.keyword.IBM_notm}} developerWorks community, such as blogs and forum questions.

After trying to find your answer or solution by searching the [{{site.data.keyword.IBM_notm}} Support Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/home/entry/portal){: new_window}, you can contact {{site.data.keyword.IBM_notm}} Support. The type of support that you have depends on your service type.

- **Free plan users**

    Get help and answers to questions by asking fellow members of the developer community. For links to developer communities, see the **Developer community** section in the table of contents.

- **Paid plan users**

    As a paid plan user, you, too, can ask questions and learn from other users' questions. The forums are open to everyone and are a great place to start. For links, see the **Developer community** section in the table of contents.

    Submit a problem ticket from the [{{site.data.keyword.IBM_notm}} Cloud Service Portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://watson.service-now.com/wcp){: new_window}.

    > **Note:** You must be authorized to submit problems to {{site.data.keyword.IBM_notm}}.

### Procedure

To contact {{site.data.keyword.IBM_notm}} Support about a problem:

1. Define the problem, gather background information, and determine the severity of the problem.
1. Gather diagnostic information, if possible.
1. Submit the problem to {{site.data.keyword.IBM_notm}} Support. For contact details, refer to the [Software as a Service support guide ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www-01.ibm.com/software/support/acceleratedvalue/SaaS_Handbook_V18.pdf){: new_window}.
