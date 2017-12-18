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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.IBM}} Marketplace. To see the documentation for the new version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/annotate-documents.html){: new_window}.
{: tip}

# Annotating documents
{: #annotate-documents}

Users who have knowledge of the industry and its language must annotate the documents.
{: shortdesc}

Perform the following tasks to enable human annotators to access the project:

- Invite subject matter experts to the {{site.data.keyword.watson}}&trade; {{site.data.keyword.knowledgestudioshort}} instance that you are using.
- Associate human annotators with the annotation set or sets that you want them to annotate.
- Create a task that assigns the human annotator to annotate the documents in the set.

    > **Attention:** It is not until you explicitly assign tasks to human annotators that they can see your project when they log in to {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}}.

Let your human annotators know that they can use the documentation in the [User Guide: Ground Truth Editor](/docs/services/knowledge-studio/user-guide.html) section for detailed information on how to use the Ground Truth Editor to annotate documents.

## Annotator component life cycle
{: #wks_lifecycle}

The annotator component that you create with {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} is a software component that can be plugged into a natural language processing (NLP) pipeline.

With {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} , you can create, evaluate, and improve annotator components for new domains. An annotator adds annotations (metadata) to text that appears in natural language content. The annotations, which identify mentions of entities of interest in your domain content, the relationships between them, and how the mentions co-reference the same entity, can be used by applications to automatically analyze and process text. Application users benefit from this level of analysis by being able to extract meaning, discover insights, and obtain answers in a natural language context.

The creation of an annotator component is an iterative multiple-step process that involves several stages: knowledge curation, ground truth generation, annotator component development, annotator component evaluation, and runtime deployment.

### End-to-end domain adaptation
{: #wks_lifecycle__wks_lifecycleS6}

The following diagram summarizes the interactions between these five stages of annotator component development and the typical activities that occur at each stage.

![A summary of the five stages of annotator development and the activities that occur at each stage.](images/wks_flow.png)

### Knowledge curation
{: #wks_lifecycle__wks_lifecycleS1}

This stage, which is external to {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} , refers to the process of selecting, collecting, preserving, and maintaining content relevant to a specific domain. Curation adds value to data; it transforms data into trusted information and knowledge.

### Ground truth generation
{: #wks_lifecycle__wks_lifecycleS2}

This stage refers to the use of {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} tools and best practices to produce a collection of vetted data that can be used to adapt a {{site.data.keyword.watson}} solution to a particular domain. The accuracy of this vetted data, called *ground truth* or *gold standard documents*, is critical because inaccuracies in the ground truth will correlate to inaccuracies in the applications that rely on it.

An essential part of teaching {{site.data.keyword.watson}} about a new domain involves providing it with knowledge about entities of interest in your domain content, the relationships between them, and how the entities co-reference each other. Collecting this knowledge includes the following activities:

- Involving domain subject matter experts to create the following resources, or to identify existing resources that can be re-used or modified for your domain:

  - Annotation guidelines and examples to help human annotators learn how words and passages in your domain content are to be annotated.
  - Type systems that define the domain-specific types (objects) and features (data classifications) that can be discovered in your domain content through text analysis. The type system controls the types of annotations that a human annotator can add to documents.
  - Dictionaries of terms that are to be treated as equivalent terms in your domain content.

- Creating a corpus of documents that are representative of your domain content.
- Pre-annotating documents based on the dictionaries that you add to a {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} project. After you create a machine-learning annotator, you can use the annotator to pre-annotate new documents that you add to the corpus. Pre-annotation is a process of machine-annotating a document to the extent possible before a machine-learning model is available to do so. Pre-annotation can reduce human-annotation labor by replacing some human annotation creation with mere verification of the correctness of machine annotation.
- Dividing documents among human annotators, who then use the {{site.data.keyword.knowledgestudiofull}} Ground Truth Editor tool to manually add annotations to small sets of documents.
- Comparing the human annotation results and resolving conflicts. Adjudication in this phase is needed to ensure accurate and consistently annotated documents are promoted to ground truth, where they can be used to train and test a machine annotator.

### Annotator component development
{: #wks_lifecycle__wks_lifecycleS3}

This stage refers to the use of {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} tools to create an annotator component. After establishing ground truth, the human annotation results can be used to train an algorithm for automatically adding annotations to large collections of documents, such as collections that include millions of documents.

### Annotator component evaluation
{: #wks_lifecycle__wks_lifecycleS4}

This stage refers to the use of {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} tools to refine the annotator component and improve performance. The results generated by the annotator component are evaluated against a test set of ground truth documents. *Accuracy analysis* identifies the causes of annotation errors. *Headroom analysis* helps you assess which errors require focus and where annotator refinements can yield the greatest impact. Adjustments can be made repeatedly to improve performance until a satisfactory level of accuracy is achieved.

### Annotator component deployment
{: #wks_lifecycle__wks_lifecycleS5}

This stage refers to exporting components that enable the annotator to run in machine-learning runtime environments and making the annotator component accessible to other {{site.data.keyword.watson}} cognitive applications. For example, you can deploy the machine-learning annotator for use by the {{site.data.keyword.Bluemix}} {{site.data.keyword.alchemyapishort}} or export the annotator for use in {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer.

## Creating an annotation task
{: #wks_hatask}

Before human annotators can begin adding annotations to documents, the annotation process manager must create an annotation task.

### About this task

The annotation task specifies which documents are to be annotated. To compare how well the human annotators perform, and to see how consistently they apply the annotation guidelines, you must include at least two human annotators in the task. In addition, some percentage of documents must occur in all of the annotation sets that you add to the task (you specify the overlap percentage when you create the annotation sets).

#### Important

- An annotation task is a temporal concept that exists to allow human annotators to annotate text in isolated spaces. It also ensures that only approved annotations are promoted to ground truth.
- An annotation set can be included in one active task at a time. To add an annotation set in one task to a different task, you must first delete the task where the annotation set is active.
- If you delete a human annotator's user account, it affects their annotations too. Any annotations in documents that were assigned to that user but were not promoted to ground truth are deleted.
- If the type system or Ground Truth Editor settings change after you create a human annotation task, you must decide whether to propagate the changes to the task. Type system changes can affect annotations; human annotators might need to review and update their documents.
- If the dictionaries change, the changes are not reflected in the current annotation task. To apply resource changes to ground truth, you must create a new annotation task.
- You can have up to 256 annotation tasks per project.

### Procedure

To create an annotation task:

1. Log in as a {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} administrator and open the **Human Annotation** page.
1. Click **Add Task**. Specify a descriptive name for the task and select the date that the task must be completed.

    > **Note:** You cannot change the task name later.

1. Click **Create**. A list of available annotation sets is displayed, along with the names of the human annotators assigned to them.
1. Select each annotation set that you want to include in the task and click **Create Task**.

    The check marks by the annotation set names make it seem like all annotation sets are selected by default, but they are not. You must explicitly select the annotation sets that you want to include.
    {: tip}

### What to do next

After the task is created, you can return to the **Human Annotation** page to view the progress of each human annotator. You can also:

- Specify preferences for using colors and keyboard shortcuts in the Ground Truth Editor.
- Specify an inter-annotator agreement threshold, and then open a task to see how consistently multiple human annotators annotated the same documents.
- Specify a URL to connect your annotation guidelines to the Ground Truth Editor.
- Check approved documents that overlap between annotation sets to resolve annotation conflicts.
- Open a task to add annotation sets to it. Ensure that the annotation sets that you add include documents that overlap with documents in the original annotation sets.

## Configuring Ground Truth Editor preferences
{: #wks_hapref}

An project manager can specify preferences for using colors and keyboard shortcuts in the Ground Truth Editor.

### Procedure

To specify visual preferences for working with the Ground Truth Editor :

1. Log in as a {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} administrator and open the **Human Annotation** page.
1. Click **Ground Truth Editor** Settings , and then on the **Entity Types** or **Relation Types** tab, you can edit type settings.
1. Select the entity type or relation type that you want to change and then click **Edit keyboard shortcuts and colors**. For each type, you can define a:

    - Keyboard shortcut, which means a user can enter `<shortcut>` to apply the type label to highlighted text. For example, if you define `o` as the keyboard shortcut for ORGANIZATION, then a user can select text, and then press the `o` key to apply the ORGANIZATION entity type to the highlighted text. If you assign an upper case letter, then the user will enter `Shift+<letter>`.
    - Text color. Ensure that the text color contrasts with the background color so the text will be visible after it is labeled.
    - Background color. This is the color of the label that is applied to the entity after you annotate it.

    When annotating documents, human annotators can use the keyboard shortcuts to quickly add annotations. And the annotation label and text colors help human annotators to instantly recognize types after they add annotations to a document.
    - If there are entity or relation types that you do not want human annotators to assign to mentions, you can hide them from the Ground Truth Editor, which shortens and simplifies the list of type options that users see. To do so, deselect the **Active** check box for the type.

    As you assign new shortcuts and colors, you can preview the changes.

1. You can also change the default selection highlight color. This is the color of the border that is displayed around text after you select it. The default color is a light blue, but you can change the color on the **Selection Highlight** tab to make it easier to identify the boundaries of the text that is selected.
1. Optional: Implement these changes in active human annotation tasks. On the **Human Annotation** page, open each task that you want to update and click **Apply Type System Updates**.

#### Related tasks

[Modifying a type system without losing human annotations](/docs/services/knowledge-studio/improve-ml.html#wks_projtypesysmod)

## Setting the IAA threshold
{: #wks_haiaathresh}

To help you decide whether to accept or reject an annotated document set, you can specify an inter-annotator agreement threshold. The threshold helps you compare how well or poorly inter-annotator agreement compares to the IAA score calculated by the system.

### About this task

To compare how different human annotators annotated the same documents, specify an evaluation threshold. If the annotations made by one human annotator differ from the annotations made by another human annotator to the point where the difference results in a low score, it means that the annotators do not agree. The disagreement needs to be investigated and resolved.

### Procedure

To set the inter-annotator agreement threshold:

1. Log in as a {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} administrator and open the **Human Annotation** page.
1. Click **IAA Settings**, specify a value between 0 and 1, such as .5 or .8, and then click **Save settings**.

## Connecting to annotation guidelines
{: #wks_haguidelines}

After you create annotation guidelines for your project, you can configure {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} to connect to them. For help with choosing the correct annotation to apply, human annotators can review the guidelines while annotating documents. Administrators can also review the guidelines if they need assistance while resolving annotation conflicts in overlapping documents.

### Procedure

To connect the Ground Truth Editor and adjudication tool to your annotation guidelines:

1. Log in as a {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} administrator or project manager, open the **Human Annotation** page, and then open the **Annotation Guidelines** tab.
1. Specify the URL to where your guidelines are hosted, either a site within your enterprise or a wiki that you previously created in {{site.data.keyword.IBM_notm}} developerWorks&reg;.
1. Click **Save**. The system connects the Ground Truth Editor and adjudication tool to your annotation guidelines. Depending on the access permissions granted to users when you created the guidelines, human annotators and project administrators might be able to update the guidelines after opening them, for example, to add clarifications and examples.

### Annotation guidelines
{: #wks_guidelines}

There is no prescribed format for how to document the guidelines, but it is important that the guidelines include detailed examples. Human annotators need to understand which entity type to apply to a mention given the context, and know which relation types are valid for a given pair of mentions. Examples drawn from your domain content are often the best way to convey the correct annotation choices to make.

Annotation guidelines are not static. As your project evolves, you'll likely discover instances of mentions and relationships that are not accurately captured in the guidelines. And you'll likely discover inconsistencies between multiple human annotators who interpret the guidelines in different ways. By updating the guidelines as situations arise, you can help improve the accuracy and consistency of annotations over time.

Before documents can be considered ground truth, any conflicts between how different human annotators annotated the same documents must be resolved. A key way to resolve the conflicts is by discussing what caused the confusion, thus helping human annotators learn from their mistakes. Improving and clarifying the guidelines can help reduce the number of conflicts and help ensure that accurately and consistently annotated documents are promoted to ground truth.

To help you manage the guidelines, you might want to divide what could become a long document into multiple parts, such as guidelines for annotating entities, guidelines for annotating relations, and guidelines for annotating the ways that mentions can be coreferenced. Changes that you make in one area must be evaluated and coordinated with changes that you make in another area. For example, if you add an entity type, review the guidelines for annotating relation types and specify how the new entity type can relate to other entity types.

#### Connecting your annotation guidelines to Watson Knowledge Studio
{: #wks_guidelines__annotguide1}

If you create annotation guidelines online, you can connect them to {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} so that users can quickly get clarification about the correct annotation to apply. After creating a project, go to the **Human Annotation** &gt; **Annotation Guidelines** page and specify the URL to where the guidelines are located. When human annotators use the Ground Truth Editor , or when administrators use the adjudication tool, they can click a link to view the guidelines.

Permission to access the guidelines is controlled by the software environment that you use to create them. To view the guidelines from within {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} , users must have read access. If you want to allow users to also update the guidelines, for example, to add clarifications or examples, you must grant those users write access.

### Annotation guidelines example
{: #wks_guidelinesexample}

Most annotation guidelines will need a lot of detail and examples to ensure that human annotators consistently annotate text.

The example presented here is a simple guideline that was created for a small domain that contains traffic incident reports.

#### Task Goals
{: #wks_guidelinesexample__annotgoals}

- As project members, become familiar with the iterative process of manual annotation and machine-learning annotator refinement.
- Annotate documents in the automotive domain with the Ground Truth Editor and use the annotations to train a machine-learning model. Annotate the entity types, relation types, and coreference the entities as needed.

#### Guideline Notations
{: #wks_guidelinesexample__annotnotation}

- Square brackets [ ] indicate the extent to be annotated when less than the entire quoted text is annotated.

    Include negations as appropriate, for example `[no injuries]ACCIDENT_OUTCOME`. The type system is not using entity class to represent negation.

#### Entity Types
{: #wks_guidelinesexample__annottype}

The type system does not use entity sub-types or roles, nor mention types or classes.

<table cellpadding="4" cellspacing="0" summary="" id="wks_guidelinesexample__table_okd_5kj_f5" class="table" width="100%" rules="rows" frame="void" border="0"><thead class="thead" align="left"><tr class="row"><th class="entry ncol thleft" valign="top" width="23.584905660377355%" id="d1735e810">Entity Type</th>
<th class="entry ncol thleft" valign="top" width="37.971698113207545%" id="d1735e812">Guidelines</th>
<th class="entry ncol thleft" valign="top" width="38.44339622641509%" id="d1735e814">Examples</th>
</tr>
</thead>
<tbody class="tbody"><tr class="row"><td class="entry ncol" valign="top" width="23.584905660377355%" headers="d1735e810 "><p class="p wrapper">ACCIDENT_OUTCOME</p></td>
<td class="entry ncol" valign="top" width="37.971698113207545%" headers="d1735e812 "><p class="p wrapper">A consequence of an accident. Applies to both humans (e.g., death) and cars (e.g., dented).
Can include "towed" and "air bag deployment" as indicators of severity of damage, and "transported
to hospital" (but not funeral home) as indicators of severity of injury. Can include
negation.</p></td>
<td class="entry ncol" valign="top" width="38.44339622641509%" headers="d1735e814 "><p class="p wrapper">"[casualty]", "[injury]", "sustained [total loss]", "[no injuries]", "[towed] due to
[disabling damage]", [not towed], "air bag did [not deploy]" (air bag itself has to be PART_OF_CAR,
related by sufferedFrom to this ACCIDENT_OUTCOME), and indications of severity.</p></td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="23.584905660377355%" headers="d1735e810 "><p class="p wrapper">CONDITION</p></td>
<td class="entry ncol" valign="top" width="37.971698113207545%" headers="d1735e812 "><p class="p wrapper">Weather or road conditions; an aspect of the scene that could affect likelihood of accident
and could change from day to day but is not about the car or driver.</p><p class="p">Can be driver error or
mechanical failure, and must appear to be problematic. Should exclude STRUCTURE.</p>
</td>
<td class="entry ncol" valign="top" width="38.44339622641509%" headers="d1735e814 "><p class="p wrapper">"dry", "rainy", "construction", "heavy traffic", "daylight", but not "grassy" or
"intoxicated".</p><p class="p">"flat tire", "overcorrected" (as in steering), "asleep", "intoxicated", "[failed to
negotiate]CONDITION a [curve]STRUCTURE", "[departed] the lane" or shoulder, but not "attempting to
pass" unless this phrase is accompanied by "without enough room" or something similar, nor
"departing the road", which is an INCIDENT.</p>
</td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="23.584905660377355%" headers="d1735e810 "><p class="p wrapper">INCIDENT</p></td>
<td class="entry ncol" valign="top" width="37.971698113207545%" headers="d1735e812 "><p class="p wrapper">An actual mention of a collision, or a car motion that is unambiguously inappropriate and
likely destructive, such as going off-road, or some other damaging incident, like a car fire. </p><p class="p">Do
not co-reference non-identical motions to each other, such as "impacted", "pushed rearward" and
"came to final rest", even if they are closely associated. </p>
<p class="p">Exclude STRUCTURE from the extent;
for example, "[came to rest]INCIDENT in a [ditch]STRUCTURE" or "[remaining in contact]INCIDENT with
the [guardrail]STRUCTURE".</p>
</td>
<td class="entry ncol" valign="top" width="38.44339622641509%" headers="d1735e814 "><p class="p wrapper"> "crash", "impacted", "overturned", "contacted", "against", "pushed", "passenger was
[ejected]", "rolled over a quarter turn" -- the quarter turn indicating severity but being part of
the incident, not an ACCIDENT_OUTCOME (do not annotate vehicle rotation).</p><p class="p">"came to final rest" in
a place the vehicle does not belong, such as an embankment or in motion from an impact, or "departed
the roadway" (not merely departing a lane, which may be a cause). </p>
</td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="23.584905660377355%" headers="d1735e810 "><p class="p wrapper">MANUFACTURER</p></td>
<td class="entry ncol" valign="top" width="37.971698113207545%" headers="d1735e812 "><p class="p wrapper">The company that makes the vehicle.</p></td>
<td class="entry ncol" valign="top" width="38.44339622641509%" headers="d1735e814 "><p class="p wrapper">Toyota, Mazda, General Motors</p></td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="23.584905660377355%" headers="d1735e810 "><p class="p wrapper">MODEL</p></td>
<td class="entry ncol" valign="top" width="37.971698113207545%" headers="d1735e812 "><p class="p wrapper">The specific kind of car, made by a specific manufacturer. Exclude any extra terms / trim
line indicators like "LX", or "SE" (e.g., only annotate "Xterra" for the phrase "Xterra
SE").</p></td>
<td class="entry ncol" valign="top" width="38.44339622641509%" headers="d1735e814 "><p class="p wrapper">Camry</p></td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="23.584905660377355%" headers="d1735e810 "><p class="p wrapper">MODEL_YEAR</p></td>
<td class="entry ncol" valign="top" width="37.971698113207545%" headers="d1735e812 "><p class="p wrapper">The model year that is part of the name of the car.</p></td>
<td class="entry ncol" valign="top" width="38.44339622641509%" headers="d1735e814 "><p class="p wrapper">'99, 2001</p></td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="23.584905660377355%" headers="d1735e810 "><p class="p wrapper">PART_OF_CAR</p></td>
<td class="entry ncol" valign="top" width="37.971698113207545%" headers="d1735e812 "><p class="p wrapper">A part of a vehicle, either inside or outside of it, regardless of whether specifically
involved in the incident. Exclude listings of capabilities of such parts. Include indications of
where in the car the part is, or something which just refers to a portion of a car without being a
specific part.</p><p class="p">Can be plural. Can include specification of position in the vehicle, such as
"[driver airbag]", "[RF door]" (meaning right-front), "[RR] passenger", "[LF and RF air bags]",
"[first row passive/automatic restraints]", "[safety system] with EDR capabilities".</p>
<p class="p">Include
towed boats, tanks, etc., except semi-trailers, which have a distinct
year/model/manufacturer.</p>
</td>
<td class="entry ncol" valign="top" width="38.44339622641509%" headers="d1735e814 "><p class="p wrapper">Cross-section, front plane, tire, steering wheel, airbag, etc.</p></td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="23.584905660377355%" headers="d1735e810 "><p class="p wrapper">PERSON</p></td>
<td class="entry ncol" valign="top" width="37.971698113207545%" headers="d1735e812 "><p class="p wrapper">Any person described in an accident scene in a report (could be a driver or a
passenger/occupant of a vehicle, pedestrian, or witness). </p><p class="p">Don't annotate adjectives, so don't
annotate "a [69-year-old] drove", but do annotate "a 69-year-old [male] drove". Can be plural, e.g.,
"LR and RF [occupants]". Excludes people who arrive after incident. </p>
<p class="p">In the absence of an
"animal" entity type, use PERSON to tag wildlife involved in / causing collisions, as their ability
to move makes them more like a PERSON than a STRUCTURE. </p>
<p class="p">Note: "passenger airbag" is a
PART_OF_CAR; it does not imply that a person is present. </p>
</td>
<td class="entry ncol" valign="top" width="38.44339622641509%" headers="d1735e814 "><p class="p wrapper">Driver, occupant, patient, child</p></td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="23.584905660377355%" headers="d1735e810 "><p class="p wrapper">STRUCTURE</p></td>
<td class="entry ncol" valign="top" width="37.971698113207545%" headers="d1735e812 "><p class="p wrapper">A structure that is on, near, or part of a road. Include specific road adjectives likely to
be relevant to the configuration of an accident; omit other adjectives.</p></td>
<td class="entry ncol" valign="top" width="38.44339622641509%" headers="d1735e814 "><p class="p wrapper">[two-lane, two-way road], [left lane], eastbound [lane], 2-foot [ditch], [right lane line],
[exit ramp], [pole], [tree], steep descending [embankment]</p></td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="23.584905660377355%" headers="d1735e810 "><p class="p wrapper">VEHICLE</p></td>
<td class="entry ncol" valign="top" width="37.971698113207545%" headers="d1735e812 "><p class="p wrapper">Any reference to vehicle other than MODEL, MANUFACTURER, and MODEL_YEAR. Can be plural, in
which case coreference is very unlikely and no part-of-group relation. </p><p class="p">Consider only vehicles
that are part of the scene; exclude emergency vehicles that responded later, for example. Bicycles
are VEHICLEs.</p>
</td>
<td class="entry ncol" valign="top" width="38.44339622641509%" headers="d1735e814 "><p class="p wrapper">"the [truck]", "the [car]", "[V1]'s"</p></td>
</tr>
</tbody>
</table>

#### Relation Types
{: #wks_guidelinesexample__annotreltype}

The type system uses relation types, but not relation classes or other attributes of relations. Negation is not encoded by a relation class, but rather by the extents of the mentions, for example, [no occupants]PERSON were [hospitalized]ACCIDENT_OUTCOME with the two mentions linked by the relation type sufferedFrom.

<table cellpadding="4" cellspacing="0" summary="" id="wks_guidelinesexample__table_z25_m4j_f5" class="table" width="100%" rules="rows" frame="void" border="0"><thead class="thead" align="left"><tr class="row"><th class="entry ncol thleft" valign="top" width="33.26996197718631%" id="d1735e923">Possible entity types for the first mention</th>
<th class="entry ncol thleft" valign="top" width="19.011406844106464%" id="d1735e925">Relation Type</th>
<th class="entry ncol thleft" valign="top" width="47.71863117870722%" id="d1735e927">Possible entity types for the second mention</th>
</tr>
</thead>
<tbody class="tbody"><tr class="row"><td class="entry ncol" valign="top" width="33.26996197718631%" headers="d1735e923 "><p class="p wrapper">VEHICLE, MODEL, MANUFACTURER [<b>2</b>]</p></td>
<td class="entry ncol" valign="top" width="19.011406844106464%" headers="d1735e925 "><p class="p wrapper">hasProperty</p></td>
<td class="entry ncol" valign="top" width="47.71863117870722%" headers="d1735e927 "><p class="p wrapper">MANUFACTURER, MODEL, MODEL_YEAR</p></td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="33.26996197718631%" headers="d1735e923 "><p class="p wrapper">PERSON</p></td>
<td class="entry ncol" valign="top" width="19.011406844106464%" headers="d1735e925 "><p class="p wrapper">occupantOf</p></td>
<td class="entry ncol" valign="top" width="47.71863117870722%" headers="d1735e927 "><p class="p wrapper">VEHICLE, MODEL, MANUFACTURER, MODEL_YEAR [<b>1</b>], PART_OF_CAR, STRUCTURE</p></td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="33.26996197718631%" headers="d1735e923 "><p class="p wrapper">PERSON, PART_OF_CAR, STRUCTURE, VEHICLE, MODEL, MANUFACTURER,
MODEL_YEAR [<b>1</b>]</p></td>
<td class="entry ncol" valign="top" width="19.011406844106464%" headers="d1735e925 "><p class="p wrapper">sufferedFrom</p></td>
<td class="entry ncol" valign="top" width="47.71863117870722%" headers="d1735e927 "><p class="p wrapper">ACCIDENT_OUTCOME</p></td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="33.26996197718631%" headers="d1735e923 "><p class="p wrapper">VEHICLE</p></td>
<td class="entry ncol" valign="top" width="19.011406844106464%" headers="d1735e925 "><p class="p wrapper">driveUnder</p></td>
<td class="entry ncol" valign="top" width="47.71863117870722%" headers="d1735e927 "><p class="p wrapper">CONDITION, ACCIDENT_CAUSE</p></td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="33.26996197718631%" headers="d1735e923 "><p class="p wrapper">PART_OF_CAR</p></td>
<td class="entry ncol" valign="top" width="19.011406844106464%" headers="d1735e925 "><p class="p wrapper">locatedOn</p></td>
<td class="entry ncol" valign="top" width="47.71863117870722%" headers="d1735e927 "><p class="p wrapper">VEHICLE, MODEL, MANUFACTURER, MODEL_YEAR [<b>1</b>]</p></td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="33.26996197718631%" headers="d1735e923 "><p class="p wrapper">ACCIDENT_OUTCOME</p></td>
<td class="entry ncol" valign="top" width="19.011406844106464%" headers="d1735e925 "><p class="p wrapper">outcomeOf</p></td>
<td class="entry ncol" valign="top" width="47.71863117870722%" headers="d1735e927 "><p class="p wrapper">INCIDENT</p></td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="33.26996197718631%" headers="d1735e923 "><p class="p wrapper">INCIDENT</p></td>
<td class="entry ncol" valign="top" width="19.011406844106464%" headers="d1735e925 "><p class="p wrapper">causedBy</p></td>
<td class="entry ncol" valign="top" width="47.71863117870722%" headers="d1735e927 "><p class="p wrapper">CONDITION, ACCIDENT_CAUSE <strong class="ph b">(reminder: requires textual evidence of the
causality)</strong></p></td>
</tr>
<tr class="row"><td class="entry ncol" valign="top" width="33.26996197718631%" headers="d1735e923 "><p class="p wrapper">INCIDENT</p></td>
<td class="entry ncol" valign="top" width="19.011406844106464%" headers="d1735e925 "><p class="p wrapper">impactPoint</p></td>
<td class="entry ncol" valign="top" width="47.71863117870722%" headers="d1735e927 "><p class="p wrapper">The PERSON, PART_OF_CAR, STRUCTURE, VEHICLE, MANUFACTURER, MODEL, or
MODEL_YEAR [<b>1</b>] that is hit or involved in the accident.</p><p class="p">impactPoint for STRUCTURE
does not include mere specifying the location of an impact that does not involve that STRUCTURE, so
it does not apply to two vehicles colliding in an [intersection]STRUCTURE, but does apply to a
vehicle striking an [embankment]STRUCTURE.</p>
</td>
</tr>
</tbody>
</table>

#### Table notes

**1** The notation VEHICLE/MODEL/MANUFACTURER/MODEL_YEAR refers to a mention of a vehicle. The last three are respectively for cases in which the text says something like "the Accord", "the Honda", or, probably rarely, "the '99". The four entity types are in priority order, so in "the driver of the '99 Honda Accord", the relation would be driver (as PERSON) occupantOf Accord (as MODEL), in which case Accord would have the hasProperty relation with both Honda and '99.

**2** MODEL and MANUFACTURER can only be the first argument of hasProperty, only when they appear as nouns (references to a vehicle). MODEL can have the relation hasProperty to MANUFACTURER and MODEL_YEAR, as in "the '99 Honda Accord drove". MANUFACTURER can only have the hasProperty relation to MODEL_YEAR, as in "the '99 Honda drove".
