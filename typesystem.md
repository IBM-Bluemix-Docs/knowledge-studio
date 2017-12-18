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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.IBM}} Marketplace. To see the documentation for the new version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/watson-knowledge-studio/typesystem.html){: new_window}.
{: tip}

# Establishing a type system
{: #typesystem}

The type system controls how content can be annotated.
{: shortdesc}

## Type systems
{: #wks_typesystem}

A type system defines things that are interesting in your domain content that you want to label with an annotation. The type system controls how content can be annotated by defining the types of entities that can be labeled and how relationships among different entities can be labeled. The annotator process manager typically works with subject matter experts for your domain to define the type system.

In {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} , you can create a type system from scratch or import an existing type system. To jump-start a project, you might want to import a type system that was created for a similar domain. You can then edit the type system to add or remove entity types or redefine the relationship types.

A sample type system based on the KLUE type system is provided for you to use with the {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} tutorials. KLUE stands for Knowledge from Language Understanding and Extraction and was derived by {{site.data.keyword.IBM_notm}} Research based on the analysis of collections of news articles. You can download a sample KLUE type system from <a target="_blank" href="https://watson-developer-cloud.github.io/doc-tutorial-downloads/knowledge-studio/en-klue2-types.json" download>here<img src="../../icons/launch-glyph.svg" alt="External link icon" title="External link icon" class="style-scope doc-content"></a>.

Many industries, such in domains like metallurgy, geology, market intelligence, life science, electronic health records, and oncology publish dictionaries or ontologies of domain-specific terminology. Consider referencing this type of resource to get an idea of the types of entities you might want to define in your own type system.

### Mentions
{: #wks_typesystem__wks_typesystemS2}

A mention is any span of text that you consider relevant in your domain data. For example, in a type system about automotive vehicles, occurrences of terms like *airbag*, *Ford Explorer*, and *child restraint system* might be relevant mentions.

### Entity types
{: #wks_typesystem__wks_typesystemS3}

An entity type is how you categorize a real-world thing. An entity mention is an example of a thing of that type. For example, the mention "President Obama" can be annotated as a PERSON entity type. The mention "{{site.data.keyword.IBM_notm}}" can be annotated as an ORGANIZATION entity type. Entities are often nouns, but can also be verbs, as long as the verb is important to capture for the purposes of the application that will use the type system. For example, EVENT_CRASH might be a valid entity type for a type system about automotive vehicles, so that the word *hit* in the sentence, "The car hit the barrier." can be annotated.

The goal of your annotation project is to annotate each mention in a document with the type of thing that it is. After a mention is classified by entity type, the labeled span of text is referred to as an entity.

A type system that you build with {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} can include the following entity type attributes. The attributes help qualify mentions in text, but they are not marked as entity types by a machine-learning annotator. For example, if the entity type ORGANIZATION has an entity subtype called COMMERCIAL, COMMERCIAL is not marked as an entity type on its own.

- **Role**

    Qualifies the mention by the context in which the mention occurs. For example, the mention "France" in the statement, "the students went to France", is marked with the entity type GPE because France is a geo-political entity. But, because France in this context is also a destination for the traveling students, the entity type is qualified by adding an attribute, in this case the role LOCATION. For another example, the mention "Lawyers" might be marked with the entity type PEOPLE and also by the role OCCUPATION.

- **Entity subtype**

    Further classifies the entity type. For example, the entity type ORGANIZATION might include the subtypes COMMERCIAL, GOVERNMENT, MILITARY, and EDUCATION.

- **Mention type**

    Qualifies the mention by certain parts of speech:
    - NAM: the mention is a proper name, such as a person's name or the name of an organization.
    - NOM: the mention is nominal (a common noun), such as company or president.
    - PRO: the mention is a pronoun, such as he, we, or it.
    - NONE: none of the other three mention types are applicable.

- **Mention class**

    Qualifies the mention by indicating whether the mention is specific, generic, or negated:
    - SPC: the mention is specific, often including the word "the" in English, such as "the book" or "the hurricane occurred in September". In these examples, the mentions "book" and "hurricane" would be annotated with the attribute SPC.
    - GEN: the mention is generic, such as "a book" or "hurricanes usually occur in the fall". In these examples, the mentions "book" and "hurricanes" would be annotated with the attribute GEN.
    - NEG: the mention is negated, such as references to "no book". When you train an annotator, the algorithm can learn from both negative and positive examples, so it's important to mark mentions of both types.

### Relation types
{: #wks_typesystem__wks_typesystemS4}

A relation type defines a binary, ordered relationship between two entities. For a relation mention to exist, text must explicitly define the relation and bind mentions of the two entities together, and must do so within a single sentence. For example, the sentence *Mary works for {{site.data.keyword.IBM_notm}}* is textual evidence of the **employedBy** relation type.

For some relation types, the order of entity mentions matters. For example, the employedBy relation type allows the entity type PERSON or PEOPLE as the first mention in the relationship, and ORGANIZATION or GPE as the second mention, but not the other way around. Mary employedBy {{site.data.keyword.IBM_notm}} is a valid relationship; {{site.data.keyword.IBM_notm}} employedBy Mary is not. For some relation types, such as spouseOf, colleague, or sibling, order does not matter. When you define a relation type where order is not important, a best practice is to add information to the annotation guidelines to regularize how the relation type is used. A convention for noting such symmetrical relations is to say that the entity mention that occurs first in the text should be the first one in the relation.

**Related concepts**:

[Importing resources from another project](/docs/services/knowledge-studio/exportimport.html)

## Adding a type system to the project
{: #wks_projtypesys}

You must create or import a type system before you begin any annotation tasks.

### About this task

The following naming rules apply to type system entries:

- Names cannot contain spaces.
- Use only the following alphanumeric ASCII characters and the underscore character in values that you add to the type system: A through Z, a through z, 0 through 9.
- The first character in an entity or relation type name must be alphabetical.
- Entity type names cannot be longer than 64 characters.
- Relation type names cannot be longer than 128 characters.

By convention, entity type names are specified in uppercase characters (ORGANIZATION) and relation type names are specified in camel case (employedBy). But, this convention is optional.

### Procedure

1. Log in as a {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} administrator or project manager and open the **Type System** page.
1. Choose one of the following methods for creating the type system:

    - To import an existing type system:

        1. Click **Import** to import an existing type system.

            If you previously exported a type system from a {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} project, the type system is exported in `JSON` format. You can import this type system to jump-start the creation of a new project. For details, see [Importing resources from another project](/docs/services/knowledge-studio/exportimport.html).

            > **Note:** Regardless of the origin of the type system, the entries in it must meet the naming rules listed earlier.

        1. Add, edit, and delete entity types and relation types the same way that you do when you create a type system from scratch.

    - To create a type system from scratch:

        1. Click **Add Entity Type**.
        1. Specify a descriptive entity type name, keeping in mind that the entity type is a label for annotating important spans of text (mentions) in your domain content. Keep the name short and representative, so human annotators can remember it easily.

            You can also optionally define roles and subtypes for the entity type:
            - A role helps qualify the entity type in the context in which the mention occurs. For example, the mention Software Engineer might be labeled with the entity type PEOPLE and, in this context, by the role OCCUPATION. See [When to define roles](/docs/services/knowledge-studio/typesystem.html#wks_typesystem_roles) for more information.
            - A subtype helps further classify the entity type. For example, the entity type GOVERNMENT might have subtypes of MILITARY and CIVILIAN.

            > **Note:** By defining a role or subtype for an entity, you are giving more options to the person who will associate type information to mentions at annotation time. The human annotator can apply an annotation that specifies the entity type only, or the entity type plus the role or subtype that you are defining now.

            Try to define enough entity types to capture the key concepts that you want to annotate, but not so many entity types that it becomes cumbersome for human annotators to apply the labels accurately.

        1. Click **Mention Attributes** to view the default mention types and mention classes (you cannot edit these values).

            The purpose of an attribute is to help label each mention by the type of thing that it is. A mention type indicates whether the mention is a name, nominal, or pronoun, and a mention class indicates whether the mention is specific, generic, or negated.

        1. Click **Relation Types** and specify how two mentions can relate to each other.

            Order between the first and second entities in a relation type is usually relevant. For example, a PERSON entity can be an employee of an ORGANIZATION entity or a geo-political entity (GPE), such as Mary employedBy {{site.data.keyword.IBM_notm}}, but organizations and geo-political entities cannot be employed by a person. When a human annotator clicks an entity in the Ground Truth Editor , the list of available relation types is controlled by what is defined in the type system.

            Do not define relation attributes. They are not used by the machine-learning model. The model uses only the relation type and order, and ignores the relation attributes.

        1. Use the **Edit** and **Delete** icons to modify entity types and their associated relation types, or to delete an entity type or relation type from the type system.

            If you delete an entity that is used in a relation type definition, the relation type definition is also deleted.

**Related tasks**:

[Modifying a type system without losing human annotations](/docs/services/knowledge-studio/improve-ml.html#wks_projtypesysmod)

## Type system creation guidelines
{: #wks_typesys_guidelines}

The purpose of any type system in {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} is to define how spans of text can be annotated. If you choose to create a type system from scratch, follow these guidelines.

Focus on creating an inventory of entity types and relation types that cover the information that is needed by the application in which the type system will be used. Do not cover things that are not needed. Do not split types or make distinctions that are not needed by the application. For example, if the source document contains the sentence *Murder on the Orient Express made headlines*, then how you define entity types to capture the key information in the sentence differs depending on the type of application that will use the model that you build with the type system.

- For a literary application, you might create types that capture this information:

    ```
               [NOVEL]           [CRITICAL_RECEPTION]
    ```
    {: screen}

    ```
    [Murder on the Orient Express] [made headlines]
    ```
    {: screen}

- For a public safety application, you might create these types:

    ```
    [EVENT_CRIME]      [LOCATION]
    ```
    {: screen}

    ```
      [Murder] on the [Orient Express] made headlines
    ```
    {: screen}

The structure is often driven by characteristics of the documents from which information will be extracted, but should always be tempered by what information the application will actually use from those documents. For example, you might be creating an application that gains insights from medical records. To build the type system, you start looking at patient records to see what kinds of information must be captured. The patient records might all contain a field that describes what the patient ate for lunch. However, if the application will not use that information, do not add it to the type system. And in making the decision to make this omission, recognize that this means that sections of your patient record documents will be left unannotated. That is alright and even expected.

Mentions annotate a span of text; they do not replace the text. A type system is not an ontology for a domain. Expect to have general entity types such as MEDICATION_NAME instead of having an entity type for each medicine type. The document text will continue to contain the specific medicine name. It will just be enhanced with an annotation that identifies its type, which makes the information easier to find and extract programmatically.

As you get started, define 10 to 40 entity types and relation types. Stay to the lower end of the range if the human annotators who will be working on the project are not highly specialized in the field. Do not define more than 50.

Plan to spend a good amount of time defining the type system before your team begins any human annotation tasks. When the team does start to annotate documents, begin with a small set, perhaps no more than 50. Annotate only mentions initially, examine the results, and refine your annotation guidelines and the type system as needed. When you're satisfied with the results of mention annotation, move on to annotate relations and coreferences.

While fundamental work is underway to define a set of entity types and mention-annotation guidelines, avoid putting a lot of effort into annotating relation mentions. Mention changes will undo relation annotation work. Do take some time to define a set of relation types and their allowable entity type pairs so that relation type needs are taken into consideration before the entity type inventory is finalized.

Expect the type system to evolve with the experience of people trying to annotate to it. If you revise the type system after you create human annotation tasks, you must decide whether to apply the changes to each task. If you apply the changes, human annotators will have to revisit the documents that they annotated previously.

When you test the annotator, you can review statistics that show how frequently the entity types and relation types occur in your sample documents. Be sure to review these statistics. To ensure that your application receives enough context to accurately annotate large collections of documents, your test data must include a large sampling of the most important entity types and relation types.

> **Important:** After you train your first annotator component, you will likely need to make modifications based on the performance statistics. However, to create a reliable statistical model for machine annotation, you want the type system to be as close to final as possible before you begin large-scale annotation tasks.

## When to define roles
{: #wks_typesystem_roles}

Using roles enables you to define more precise entity types.

Every entity that you add has a role. Unless you change it, the role name is the same as the entity name. You can choose to define a different role for an entity to capture a more nuanced usage of the mention. The word or phrase to which the role applies is literally an example of an entity type, but in the sentence it plays the role of another entity type. For example, in the phrase, *the White House vetoed the bill*, we can capture more precisely the meaning of the *White House* if we annotate both the entity type of FACILITY, and a role of ORGANIZATION or PERSON. White House is a building (FACILITY), but represents the government (ORGANIZATION) or the President of the United States (PERSON) in this construction. The entity type + role label creates a more precise classification of the mention in the text.

Roles can also provide you with a way to capture relation information without relying on the use of overlapping mentions. For example, you might want to annotate the text *31-year-old male* such that it captures the idea that this is a reference to a person with the attribute age of 31 years and attribute gender of male. By examining the text, we determine that *31-year-old* is an age, *male* is a gender, and together they signify a person. You are dealing with 3 entity types, basically: AGE, GENDER, and PERSON. One approach to representing this would be to annotate *31-year-old* as AGE, *male* as GENDER, and because the distinct mention of a PERSON is missing, but *male* has come to represent person, the word *male* can have a role of PERSON. You can then capture relations between the PERSON role and all the attributes of a person that you want to capture. For example, you can define a hasAttribute relation between the PERSON role and AGE mention. Because you applied both a GENDER entity type and a PERSON role type label to the same word *male*, you cannot define a hasAttribute relation between the two. However, the fact that the two labels are applied to the same mention associates them with one another. This association is considered by the machine learning annotator without you having to define a hasAttribute relation type to explicitly call out the relationship.

A similar example is when the phrase *2008 Ford F-150* is used as shorthand for *2008 Ford F-150 truck*. Here, *2008* is annotated as a MODEL_YEAR entity type, *Ford* is annotated as a MANUFACTURER entity type and *F-150* is given a MODEL entity type. But with the word "truck" missing, *F-150* also represents a vehicle. Saying *the F-150* is like saying *the truck*. You can capture that usage by adding a VEHICLE role to the mention in addition to its MODEL entity type. You can then define hasAttribute relations between the VEHICLE role and the MANUFACTURER and MODEL_YEAR entity mentions.

### How are roles different from subtypes?

Entity subtypes are for stratifying an inventory of entity types into a hierarchy. For example, if you care to distinguish 40 things, but they logically group into 10 sets of 4 (VITALSIGN_BLOODpreSSURE, VITALSIGN_HEARTRATE, MEDICATION_DOSAGE, MEDICATION_FREQUENCY), you could structure them into types and subtypes, which yields more compact menus, but adds a level of depth and nuisance to the labeling process. For the purposes of information extraction, a combination of types and subtypes is interchangeable with lots and lots of types with no subtypes. By contrast, the word or phrase to which you apply a role is an example of one entity type, but it plays the role of another entity type, and one that is not a subtype of the other.

### How are roles treated?

The {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} machine learning annotator defines classifier labels for each mention of an entity that it finds in the source documents by concatenating the entity type + role values. When you provide role values, you create more precise labels. Each group of instances of one label type that are found in the training data forms a more uniform set of mentions. The challenge is that by choosing to be more precise, you must also accede to providing more training data to ensure that the model performs well. But, the more training data you provide, the better the model becomes. So, if you don't mind doing additional annotation, using roles gets you better results.

As an example, let's assume that the following sentences occur in a source document, and we want to capture the "Acme" (where Acme is a well-known truck manufacturer), "sedan", and "truck" as similar entities because they all refer to a physical vehicle:

- a) The Acme crashed into the concrete barrier.
- b) The sedan crashed into the concrete barrier.
- c) The Acme A-160 truck crashed into the concrete barrier.

You can handle the type system design in two ways:

1. Define two entity types: **MANUFACTURER** and **VEHICLE**. For the **MANUFACTURER** entity, define a **VEHICLE** role that can be used in addition to the default **MANUFACTURER** role.

    Using this type system, the sentences are annotated as follows:
    - a) The "Acme" is annotated as a **MANUFACTURER** entity, but with a role of **VEHICLE**, since it refers to an actual vehicle. So, its internal label is **MANUFACTURER-VEHICLE**.
    - b) The "sedan" is annotated as entity type **VEHICLE**. It is automatically assigned the **VEHICLE** role, since no other role is defined.
    - c) The "Acme" is annotated as entity type **MANUFACTURER** and "truck" is annotated as entity type **VEHICLE**. No roles are assigned, so the default roles are used.

1. Define two entity types only without roles: **MANUFACTURER** and **VEHICLE**.

    Using this type system, the sentences are annotated as follows:
    - a) The "Acme" is annotated as entity type **VEHICLE**.
    - b) The "sedan" is annotated as entity type **VEHICLE**.
    - c) The "Acme" is annotated as entity type **MANUFACTURER** and "truck" is annotated as entity type **VEHICLE**.

How do the two different type systems perform? Let's assume that a set of documents were annotated by human annotators. After the annotation pass, the following training events, which are manually labeled entities, are identified in the training corpus:

- **Type system 1**

    ```
    MANUFACTURER-MANUFACTURER 800 events
    MANUFACTURER-VEHICLE 200 events
    VEHICLE-VEHICLE 400 events
    ```
    {: screen}

- **Type system 2**

    ```
    MANUFACTURER 800 events
    VEHICLE 200 + 400 = 600 events
    ```
    {: screen}

When the model processes new documents, it is likely that "Acme" will be labeled as a MANUFACTURER most of the time because the spelling of a word is a strong feature and the word "Acme" will probably be defined in the MANUFACTURER dictionary. It would take a lot of context to label it differently. If we use type system 1, there are only 200 MANUFACTURER-VEHICLE training events, which is a disadvantage when compared to the 600 events of VEHICLE in type system 2. However, the training event clusters in type system 1 are all quite uniform, which leads to better performance. For type system 2, the set of 600 training events for VEHICLE is actually composed of two rather disjoint clusters: one contains manufacturer names that refer to actual vehicles, such as "Acme" and "Ford", and the other contains vehicle types, such as "sedan", "SUV", and "truck". Intuitively, each of these two clusters themselves are uniform, but by mixing them together, it dilutes the training cluster and presents a tougher problem to solve. If you keep doing annotation and adding more training events, performance in type system 1 keeps getting better, whereas, the problem of resolving two disjoint clusters that you get with type system 2 does not improve with more training.
