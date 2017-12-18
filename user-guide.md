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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.IBM}} Marketplace. To see the documentation for the new version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/user-guide.html){: new_window}.
{: tip}

# Annotating documents
{: #user-guide}

The information in this section helps subject matter experts who have been asked to annotate industry documents use the Ground Truth Editor to complete the task.
{: shortdesc}

## Project access
{: #wks_access_for_annotator}

You cannot see any projects until someone else creates a project and gives you access to it.

When an administrator adds you to an instance of {{site.data.keyword.watson}}&trade; {{site.data.keyword.knowledgestudioshort}} , you are added in the human annotator role. As a human annotator, you cannot create a project or even see projects that were created by others at first. To get access to a project, the administrator must create a project. Then the administrator or a project manager that the administrator associates with the project must perform the following steps:

1. Create an annotation set and associate you with it.
1. Create a task that assigns you to annotate the documents in the set.

It is not until an annotation task is assigned to you that you can see the project.

If you were invited to participate in a {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} project, but do not see any projects from the Projects page, contact the person who invited you, and ask him to perform the steps described earlier.

## Annotation best practices
{: #wks_anno_bp}

These annotation best practices provide some guidance and examples as you start to annotate documents.

- Annotate all documents completely.

    Machine learning learns from negative examples -- what is not annotated -- not just from what is annotated. So, be judicious in what you annotate, but do a complete job. If you carefully annotate only the first 5 of 10 documents in a set, the annotations that you do not capture in the last 5 documents will teach the model to ignore any entity or relation mentions that were missed in those documents. You could end up reversing any gains you made by doing a thorough job with the first 5 documents.

- Consistent annotation is at least as important as correct annotation.

    Some decisions regarding annotation guidelines are arbitrary, like whether car trim lines should be considered part of model names, such as *Camry* or *Camry LX*. Which of the policies is chosen is far less important than that the project team agrees on one or the other and annotates in accordance with that policy consistently.

- Label entity mentions on word-token boundaries only, because mention-detection search works at the word-token level of granularity.
- Label entity mentions that are limited to one or two adjacent words whenever possible.

    Doing so is not always possible or easy. Consider these examples:
    - The source document contains a sentence from which, for the purposes of the application that will use the type system, we want to annotate the problem and its cause.

        ```
        The electronic module was burnt because the wrong voltage was applied.
        ```
        {: screen}

        One might be tempted to annotate the problem and cause like this:

        ```
                    [PROBLEM]                           [CAUSE]
        ```
        {: screen}

        ```
        [The electronic module was burnt] [because the wrong voltage was applied].
        ```
        {: screen}

        However, it is not a good practice to annotate such long phrases as entity types. Instead, find the entities of importance and identify how they are associated with one another by defining a relation mention.

        ```
               [LOCATION]          [SYMPTOM]                [CAUSE]
        ```
        {: screen}

        ```
        The [electronic module] was [burnt] because the [wrong voltage] was applied.
        ```
        {: screen}

        ```
                      ^---isStatusOf--| |------causedBy-------^
        ```
        {: screen}

    - The source document contains a split verb that you want to annotate. How do you annotate noncontiguous text as a single entity type? You can annotate each entity mention, and identify them as being related to each other by using a relation mention.

        ```
                  [EVENT_ANSWER]      [EVENT_ANSWER]
        ```
        {: screen}

        ```
        All of the phones were ringing, but he knew he should [pick] the red phone [up] first.
        ```
        {: screen}

        ```
                            ^----splitType-----^
        ```
        {: screen}

- Avoid overlapping mentions, which are two different entity type labels that are applied to a single phrase in a document. For example, given the sentence, *She donated her father's journals to the JFK Library.*, you would overlap mentions if you annotate JFK=PERSON and JFK Library=LOCATION for the single phrase *JFK Library*. The use of the term is more about the library than the person in this sentence, so only the latter annotation should be applied.

    Decoding such structures requires multiple parallel invocations of a machine-learning model because mention detection only looks for a single label or no label on each word token.

- Determine how the team will handle lists and plurals in running text. For example, the KLUE type system has PERSON and PEOPLE entity types that distinguish the singular from the plural. You can choose to annotate the list *Barack, Michelle, Malia, and Sasha Obama*, in one of the following ways:

    - Annotate each item in the list as a singular entity mention (*Barack*, *Michelle*, *Malia*, and *Sasha Obama* are each a PERSON mention)
    - Annotate the whole phrase as one plural entity mention (*Barack, Michelle, Malia, and Sasha Obama* is a single PEOPLE mention).

    No one approach is necessarily better than the other; but be sure your team chooses one of them, and applies it consistently to any lists that occur in the documents.

- A coreference is used when mentions refer to the same real-world entity. Relations are used between distinct entities. So, no two mentions should be connected by both coreference and a relation.

## Annotation with the Ground Truth Editor
{: #wks_hagte}

When a human annotator annotates a document, the document is opened in the Ground Truth Editor. The Ground Truth Editor is a visual tool that human annotators use to apply labels to text.

The goal of human annotation is to label mentions, relations, and coreferenced mentions so that the machine-learning annotator can be trained to detect these patterns in unseen text. At a minimum, use the tool to annotate entity mentions. If the application that will use the resulting model does not need to find and extract coreferences and relation mentions, then you do not need to annotate coreferences and relation mentions.

Concordance is an optional tool that can be used by human annotators to expedite the annotation of repetitive mentions.

Choose a mode to use when manually annotating documents:

- **Mention mode**

    In this mode, the human annotator associates entity types, as defined in the type system, with meaningful words or phrases in the text. For example, all mentions of person names might be associated with an entity type named PERSON. The annotation of mentions is required and must occur before you annotate relation types and mentions as coreferences.

    The human annotator can optionally use the concordance tool to ensure that the same text is annotated with the same entity type throughout a document and across annotation sets.

- **Relation mode**

    In this mode, the human annotator connects mentions by associating a relation type, as defined in the type system. For example, the mention John Smith might be connected to the mention {{site.data.keyword.IBM_notm}} by the relation type employedBy. The annotation of relation types is optional and can occur before or after you annotate mentions as coreferences.

- **Coreference mode**

    In this mode, the human annotator identifies mentions that mean the same thing, thus helping to ensure consistency in the annotations when words are not identical. For example, the mention of {{site.data.keyword.IBM_notm}} in the first sentence, the mention of International Business Machines, and the mention of {{site.data.keyword.IBM_notm}} in a later sentence refer to the same thing and would all be labeled by the same entity type, such as ORGANIZATION. The annotation of mentions as coreferences is optional and can occur before or after you annotate relation types.

### Tips for using the editor

- Save your work as you go.
- If you make a mistake, you can press **Ctrl+Z** to undo the previous action. To redo the action after undoing it, press **Ctrl+Y**. You can undo the previous 10 actions that you performed while editing the current document; they are lost as soon as you close the document. The actions must be undone in reverse order, and you must switch to the mode that you were in when you performed the action to undo it. You cannot undo and redo concordance tool actions.

## Annotating entity mentions
{: #wks_haentity}

To annotate entity mentions, a human annotator selects a string of text in a document, and then applies a label that most appropriately describes what the string of text represents. The labels that can be applied are entity types defined in the project's type system.

### Before you begin

Click the image to see how to annotate an entity mention.

<div id="wks_haentity__imagemap_z5h_4w1_kw">
  <img usemap="#d42107e324" border="0" class="image" src="images/annotate-mention.jpg" alt="Shows a document open in the ground truth editor." />
  <map name="d42107e324" id="d42107e324">
    <area href="entity-gif.html" alt="" title="" shape="rect" coords="0,0,955,250" />
  </map>
</div>

### About this task

Before starting to annotate entity mentions in a document, it's a good practice to read the entire document. Doing so can help keep the entire context in mind while annotating, and can help provide insights into how entity mentions might relate to each other and which mentions might need to be coreferenced in future passes through the document.

When you open a document to annotate it, you might want to use the concordance tool to annotate repeating entity mentions first, and then annotate individual entity mentions. You can then annotate relation mentions and coreferences in any order that you like, or not at all. Entity mention annotation is mandatory. Whether you also annotate relation mentions and coreferences depends on the purpose of your annotator component and the needs of your domain. However, until and unless you identify coreferences, each entity mention is considered to represent a distinct entity.

#### Tips

- Keep in mind that shorter entity mentions are better for training because it is easier for the machine-learning annotator to recognize the shorter patterns and add the correct annotation tokens.
- If you chose to use a dictionary-based tokenizer with the project, and want to handle compound terms and punctuation in your training data, you can add the terms to a dictionary and create a dictionary annotator to pre-annotate the occurrences. For example, to avoid sentence boundary breaks for terms that include punctuation, add terms like Yahoo! and Dr. to a dictionary. Likewise, if your training data includes hyphenated words or alphanumeric acronyms, like Hi-C or MS-60-70, add those terms to the dictionary. To annotate occurrences regardless of case, add the terms in lowercase (such as hi-c). To annotate variations, add the variations as surface forms (MS-60-70 and MS 60 70). **Important**: Do not use this approach if you are using the default tokenizer.

### Procedure

To annotate entity mentions in a document:

1. Log in as a human annotator (or as an administrator who was assigned documents to annotate). Projects that contain tasks that are assigned to you are displayed.
1. Open a project and then open the task that you want to work on. The annotation sets that are assigned to you are displayed.
1. Click **Annotate** to open an annotation set in the Ground Truth Editor.
1. After the list of documents is displayed, click a document to open it. By default, the document opens in **Mention** mode, which is the mode you use to annotate entity mentions.
1. To annotate an entity mention:

    1. Click a word in the text that you recognize as a mention of a particular entity type from the type system. For entity mentions that consists of more than one word, click another word or drag the selection box edges to select multiple words or compound words.
    1. Either select the entity type that you want to apply from the pane on the right, or enter the keyboard shortcut for the entity type.

        If annotation guidelines were previously connected to the project, and you want help with choosing the correct annotation to apply, click **View Guidelines**. Depending on the access permissions set up on the site where the guidelines are hosted, you might be able to update the guidelines after you open them, for example, to add clarifications and examples.
        {: tip}

    1. Avoid creating overlapping mentions. But, if a valid overlapping mention is required, click **Replace** to more easily add it. An overlap occurs when you apply more than one label to an entity mention. Review these suggestions:

        - Annotate Sub-Saharan as a single mention, not just Saharan or just Sub.
        - Do not create an overlapping PERSON annotation for the *JFK* reference in *JFK International Airport*. The entire *JFK International Airport* mention should be labeled as a FACILITY only.
        - For the text *CEOs*, do not create a PERSON annotation for *CEO* and a PEOPLE annotation for *CEOs*. Annotate *CEOs* as a PEOPLE entity type only.

        Typically, the existence of too many overlapping mentions means that the annotation guidelines are ambiguous and need to be improved to provide better examples of how to handle compound words in your source data.

    1. To remove an annotation that you just added, press **Ctrl+Z** to undo the action. To remove an entity mention later, you can left-click a mention and press the **Delete** key, or click **View Details**, and then click **X** next to the entity type that is assigned to the mention.

1. Depending on the type system, you might be able to configure attributes for an entity mention, such as assigning an entity role or subtype or a mention class or type. If so, select a mention and click **Attribute View**.

    Click the image to see how to apply a subtype attribute to an entity mention.

    <div id="wks_haentity__imagemap_mjt_4d5_jw">
      <img usemap="#d42107e455" border="0" class="image" src="images/mention-attributes.jpg" alt="Shows an annotated document open in the ground truth editor." />
      <map name="d42107e455" id="d42107e455">
        <area href="entity-gif0.html" alt="" title="" shape="rect" coords="0,0,675,310" />
      </map>
    </div>

1. Click **Save** at any time to save your work.

### What to do next

After you finish annotating all entity mentions, relation mentions, and coreferences in the document, as applicable, change the document status from **In Progress** to **Completed**, click **Save**, and then close the document.

After you finish annotating all documents and mark them **Completed**, the status of the annotation set changes to **Submitted**. That is how project managers know that they can start to evaluate the documents for inter-annotator agreement, and reject them or accept them and promote them to ground truth.

## Annotating repeating mentions
{: #wks_haconcordance}

You can optionally use the concordance tool to label multiple occurrences of a mention at once. The tool enables you to annotate the same text with the same entity type throughout a document and across annotation sets. Using the tool helps to ensure consistency in annotation across multiple documents. For example, you can label each occurrence of the mention "encryption" individually in mention mode, or you can label all occurrences of the mention "encryption" by using the concordance tool. Either way, the annotator component learns from the entity type that you apply to the mention.

### Before you begin

Click the image to see how to use the concordance tool to find and annotate all mentions in a document.

<div id="wks_haconcordance__imagemap_zbn_r25_jw">
  <img usemap="#d42107e528" border="0" class="image" src="images/concordance.jpg" alt="Shows an annotated document open in the ground truth editor." />
  <map name="d42107e528" id="d42107e528">
    <area href="concordance-gif.html" alt="" title="" shape="rect" coords="0,0,995,435" />
  </map>
</div>

### About this task

Although the concordance tool is optional, a good practice is to use the concordance tool to annotate mentions within a document or across documents before you start annotating mentions in individual documents. When you apply an entity type to a mention with the concordance tool, the system applies the entity type to all matching mentions, overriding any existing entity types that are assigned to a matching mention. To avoid conflicts, attributes (such as roles or subtypes) are removed from existing entity types when a new entity type is applied by the concordance tool.

### Procedure

To annotate repeating mentions:

1. Log in as a human annotator (or as an administrator or project manager who was assigned documents to annotate). Projects that contain tasks that are assigned to you are displayed.
1. Open a project and then open the task that you want to work on. The annotation sets that are assigned to you are displayed.
1. Click **Annotate** to open an annotation set in the Ground Truth Editor.
1. After the list of documents is displayed, click a document to open it. By default, the document opens in **Mention** mode.
1. If you have not added any annotations yet, add at least one annotation. Select a word or word phrase that represents a mention of an entity type from your type system, and assign the appropriate type to it. Click **Save** to save your annotation.
1. Select a single occurrence of repeating text that you want to annotate, and then click **Concordance** to open the **Concordance** tool.
1. Select the documents that you want to apply the selected entity type to. You can create the annotations in all documents that you have been assigned to annotate, all documents that you have begun annotating, or all documents that you have not yet started to annotate. Click **Preview** to see the annotations that will be added.
1. If you want to view the annotations in greater context, click the icons to preview the document content or open the document in a new window.
1. Click **Apply and Review** to apply the selected entity types to mentions in the selected documents. You still have a chance to review the annotations that will be added. If an annotation is inaccurate in a particular context, you can remove that occurrence by clicking the Edit icon, and then removing the entity type assignment for the mention.
1. When you are happy with the list of annotations, click **Go Back to Ground Truth Editor** .

### Results

The mentions are annotated in the document. There is no way to remove the set of mentions that you added through concordance at once. You must remove each mention, one at a time.

## Annotating mentions as coreferences
{: #wks_hacoref}

To annotate mentions as coreferences to the same entity, a human annotator selects every occurrence of a mention that refers to the same thing. Coreference helps an annotator component recognize that entities that are referred to in different ways are to be associated with the same entity, such as the name of a U.S. state and its abbreviation, the name of a company and its acronym, or a person's name and a pronoun that refers back to that person.

### Before you begin

You must annotate mentions in the document before you can identify coreferences.

Click the image to see how to create a coreference chain.

<div id="wks_hacoref__imagemap_x35_l25_jw">
  <img usemap="#d42107e637" border="0" class="image" src="images/coref.jpg" alt="Shows an annotated document open in the ground truth editor." />
  <map name="d42107e637" id="d42107e637">
    <area href="coref-gif.html" alt="" title="" shape="rect" coords="0,0,855,335" />
  </map>
</div>

### About this task

When you annotate mentions as coreferences, the system creates a coreference chain. The chain provides a way for you to view all of the mentions in context and verify that all of the occurrences belong together under the same entity. For example, "Barack", "Michelle", "he", and "she" are all of the same entity type, PERSON, but "Barack" and "he" are one entity, and "Michelle" and "she" are another entity. In this example, you create two coreference chains.

When you create a coreference chain, you must select mentions that have been marked by the same entity type. In some cases, however, you might want to include mentions of different types in the same coreference chain. To do this, you must create multiple chains and then merge them. For example, think about how people progressively use shorthand to avoid repeating things in text. In a traffic incident report, the first reference to a vehicle might be "2004 Honda Accord Sedan". Later, the author might refer to the vehicle as "Accord", and then later refer to the vehicle as simply "vehicle". If the type system includes entries for vehicle manufacturer, model, and type, you could create multiple coreference chains per entity type, and then merge them to create a consolidated chain. The merged chain helps train the machine-learning annotator to recognize that all of these mentions refer to the same thing.

Another way to combine mentions of different entity types is to create a chain with mentions of one entity type. You can then click a mention of another entity type, and then click the chain that you created to add the mention to that chain.

Depending on your annotation guidelines, you might want to create coreference chains for verbs as well as nouns if the verbs mention the same instance of an action. For example, if two mentions of the verb "encrypts" refer to the same occurrence of encryption, you might coreference the mentions. But if one reference to "encrypts" is a general reference, or if the two occurrences refer to two different acts of encryption, you would not coreference them. If two different verbs refer to the same occurrence of an action, you might want to coreference the mentions. For example, in the statement, "He encrypted the document, and after that processing he sent the file ... ", the mentions "encrypted" and "processing" could be coreferenced because they refer to the same instance of an action.

What's most important is consistency. Decide on how you want annotate coreference and specify the rules, with examples, clearly in your annotation guidelines.

### Procedure

To annotate mentions as coreferences:

1. Click **Coreference** to switch to **Coreference** mode.
1. To create a coreference chain:

    1. Move through the document and click each mention that means the same thing and is labeled by the same entity type. For example, click each occurrence of {{site.data.keyword.IBM_notm}}, International Business Machines, and {{site.data.keyword.IBM_notm}} Corp., assuming all of these mentions have the entity type ORGANIZATION.
    1. Double-click the last mention that you want to add to the chain. A coreference chain is created in the side panel. The name of the chain matches the first mention that you selected.
    1. To highlight all mentions in a chain to review them in context, hover over the chain in the side pane.

1. The Single Mention List displays terms in the document that have been annotated, but have not been added to a chain. If you notice a mention in the list that belongs in a chain, you can add it to the chain from here.

    1. From the Single Mention List in the side panel, click the mention.
    1. From the drop-down list below the mention description, choose the number that represents the chain that you want to add the mention to.
    1. Click **Merge** to add the mention to the chain, and then click **OK**.

    The mention is removed from the Single Mention List and the number of the chain that it now belongs to is displayed below the mention in the document.

1. To remove a coreference chain that you just added, press **Ctrl+Z** to undo the action. To remove a coreference chain later, from the Coreference Chains side panel, click the **X** next to the chain that you want to remove. To remove a single mention from the chain, click the coreference ID to open a window that displays a list of the mentions in the chain, and then click the **X** next to the mention that you want to remove.
1. Click **Save** at any time to save your work.

### What to do next

After you finish annotating all entity mentions, relation mentions, and coreferences in the document, as applicable, change the document status from **In Progress** to **Completed**, click **Save**, and then close the document.

After you finish annotating all documents and mark them **Completed**, the status of the annotation set changes to **Submitted**. That is how project managers know that they can start to evaluate the documents for inter-annotator agreement, and reject them or accept them and promote them to ground truth.

## Annotating relations
{: #wks_harelation}

To annotate relation mentions, a human annotator finds textual evidence of a relation between two entity mentions in a sentence, and then applies a label that most appropriately describes the relation type. The labels that can be applied are relation types defined in the project's type system.

### Before you begin

You must annotate entity mentions in the document before you can define relation types between them.

Click the image to see how to annotate a relation mention between two entity mentions.

<div id="wks_harelation__imagemap_i5g_h25_jw">
  <img usemap="#d42107e779" border="0" class="image" src="images/annotate-relation.jpg" alt="Shows a document open in the ground truth editor." />
  <map name="d42107e779" id="d42107e779">
    <area href="relation-gif.html" alt="" title="" shape="rect" coords="0,0,990,385" />
  </map>
</div>

### About this task

The relation mention can only be defined if the text explicitly describes the relationship between the two entity mentions. Explicit textual evidence might include possessives, subject-verb-object structures, or appositives. For example, in the following sentence, it is not valid to add the **ownedBy** relation mention between *dog* and *owner*.

<pre><code>NOT VALID: The <u>dog</u> got a treat from its <u>owner</u>.</code></pre>

The valid relation mention is between *its* and *owner*, because it is this part of the sentence in which the text explicitly defines the relationship between the dog and its owner. *Owner* might be a home owner, or the owner of some other dog, but this text makes it clear that the same dog that is mentioned in the beginning of the sentence is owned by this person.

<pre><code>VALID: The dog got a treat from <u>its</u> <u>owner</u>.</code></pre>

<pre><code>                                |ownedBy^</code></pre>

The requirement that both entity mentions and the text that defines the relation type between them must exist within a single sentence might seem strict. However, keep in mind that, as in the above example, as long as you also identify coreferences in the document, you can identify relation mentions in sentences that contain words that serve as more informal entity mentions, such as pronouns. For example, the second sentence in *Mary is a scientist. She works for {{site.data.keyword.IBM_notm}}.* contains valid textual evidence of an **employedBy** relationship between Mary and {{site.data.keyword.IBM_notm}}. The coreference, *She*, is understood to be a reference to the PERSON entity type *Mary*. It is the identification of a coreference between *Mary* and *She* plus the identification of a relation mention between *She* and *{{site.data.keyword.IBM_notm}}* together that fully captures this relationship. The correct way to annotate the relation mention is like this:

<pre><code>Mary[<i>#1</i>] is a scientist. <u>She</u>[<i>#1</i>] works for <u>IBM</u>.</code></pre>

<pre><code>                         |----employedBy----^</code></pre>

where the subscript [<i>#1</i>] indicates that *Mary* and *She* are both members of the first coreference chain in the document.

### Procedure

To annotate relation mentions between entity mentions in a document:

1. Click **Relation** to switch to **Relation** mode.
1. To annotate a relation:

    1. Click an entity mention in the text, and then click a second entity mention in the same sentence that you want to connect to the first mention.
    1. Either select the relation type that you want to apply from the pane on the right, or enter the keyboard shortcut for the relation type. The list of available relation types is constrained by the first entity mention that you select, and further constrained by the second entity mention. In some cases, only one relation type remains; you still must explicitly select the relation type to apply it.

        If annotation guidelines were previously connected to the project, and you want help with choosing the correct annotation to apply, click **View Guidelines**. Depending on the access permissions set up on the site where the guidelines are hosted, you might be able to update the guidelines after you open them, for example, to add clarifications and examples.
        {: tip}

1. To remove a relation mention that you just added, press **Ctrl+Z** to undo the action. To remove a relation mention later, you can left-click the relation type and then press the **Delete** key or click **X** next to the relation type.
1. Depending on the type system, you might be able to configure attributes for a relation, such as assigning a relation tense, modality, or class. If so, select a relation label and click **Attribute View**.
1. Click **Save** at any time to save your work.

### What to do next

After you finish annotating all entity mentions, relation mentions, and coreferences in the document, as applicable, change the document status from **In Progress** to **Completed**, click **Save**, and then close the document.

After you finish annotating all documents and mark them **Completed**, the status of the annotation set changes to **Submitted**. That is how project managers know that they can start to evaluate the documents for inter-annotator agreement, and reject them or accept them and promote them to ground truth.

## Related information

[Dictionaries](/docs/services/knowledge-studio/dictionaries.html)

[Troubleshooting the Ground Truth Editor](/docs/services/knowledge-studio/user-guide-help.html)

[Type systems](/docs/services/knowledge-studio/typesystem.html)
