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

# Building the ground truth
{: #build-groundtruth}

The objective of the annotation project is to obtain ground truth, the collection of vetted data that is used to adapt {{site.data.keyword.watson}}&trade; to a particular domain. In {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} , human annotators, who are typically experts in the subject matter of the target domain, play a major role in determining ground truth.
{: shortdesc}

A typical workflow includes the following steps:

1. Human annotators submit annotated documents for review.
1. The project manager (who may be a senior domain expert) reviews the accuracy of their work and compares how consistently the human annotators annotated documents that overlap between the annotation sets.
1. If the inter-annotator agreement score is too low, the project manager rejects the annotation set and returns it to the human annotator to be improved. When an annotation set is rejected, all documents in the set are placed back into editable mode.
1. If the project manager approves an annotation set, documents that do not overlap across annotation sets are promoted to ground truth so that the annotations can be used to train the annotator component.
1. The project manager reviews the overlapping documents and resolves the annotation conflicts. At this stage, referred to as adjudication, the team might review and revise the annotation guidelines to help clarify misunderstandings that caused text to be incorrectly or inconsistently annotated by different human annotators.

    In some cases, a project manager might want a higher percentage of overlap for evaluating inter-annotator agreement than the percentage of overlap for adjudicating differences. For example, if inter-annotator agreement looks OK, then the project manager might decide that it is OK to promote either annotation to ground truth.

1. As the project manager resolves annotation conflicts, the approved annotations are promoted to ground truth.

Keep in mind that human annotation always requires judgment calls. The annotation guidelines can do a lot to ensure that text is correctly and consistently annotated, but even the best guidelines are open to interpretation by humans. To obtain ground truth, you will want to spend time training and educating human annotators so that they can make the best judgments when analyzing domain content.

## Inter-annotator agreement
{: #wks_haiaa}

After human annotators have annotated the documents, you must determine which documents to promote to ground truth. Start by reviewing the inter-annotator agreement scores. Documents with low scores are candidates to be rejected and returned to the human annotator for improvement.

When calculating inter-annotator agreement scores, the system examines all overlapping documents in all annotation sets in the task, regardless of the status of the sets. Because you cannot accept or reject annotation sets until they are in the Submitted status, you might not want to evaluate inter-annotator agreement until all annotation sets are submitted, or you might want to limit your review to only the human annotators who submitted their completed annotation sets.

The inter-annotator agreement scores show how different human annotators annotated mentions, relations, and coreference chains. You can view the scores by comparing a pair of human annotators (for example, compare all of John's mention annotations to all of Mary's mention annotations). You can also view the scores by comparing specific documents (for example, compare the relation annotations that John made in one document to the relation annotations that Mary made in the same document).

To help you identify areas that require investigation, scores that fall below the value that you specified for the inter-annotator agreement threshold are highlighted in red. In early stages of your annotation project, you might find that relation scores are often worse than mention scores because a perfect relation annotation requires that the mentions that define the relationship be in agreement first.

The score in the **All** column is a *Fleiss Kappa score*. It represents how consistently the same annotation was applied by multiple human annotators across all overlapping documents in the task. The value, which can range up to 1 and even be negative, can help you identify weaknesses in the annotation guidelines or particular human annotators. The following guidelines (*Landis and Koch, 1977*) provide a starting point for assessing overall performance:

<table cellpadding="4" cellspacing="0" summary="" id="wks_haiaa__table_p5s_dx1_f5" class="table" rules="rows" frame="void" border="0"><thead class="thead" align="left"><tr class="row"><th class="entry ncol thleft" align="left" valign="top" id="d12741e148">Score</th>
<th class="entry ncol thleft" align="left" valign="top" id="d12741e150">Agreement level</th>
</tr>
</thead>
<tbody class="tbody"><tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">&lt; 0</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Poor</p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.01 - .20</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Slight</p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.21 - .40</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Fair</p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.41 - .60</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Moderate</p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.61 - .80</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Substantial</p></td>
</tr>
<tr class="row"><td class="entry ncol tdleft" align="left" valign="top" headers="d12741e148 "><p class="p wrapper">.81 - 1.0</p></td>
<td class="entry ncol tdleft" align="left" valign="top" headers="d12741e150 "><p class="p wrapper">Perfect</p></td>
</tr>
</tbody>
</table>

The score in the other columns is an *F1 measure*. It represents the level of annotation consistency between a pair of human annotators. The value can range from 0 to 1, where perfect agreement is indicated by the score 1. What constitutes an acceptable level of agreement depends on your domain data and type system. But to provide an example, here are the F1 thresholds that project managers expect to be met or exceeded in projects that are based on the KLUE type system:

- Mentions with entity types: 0.85
- Relations: 0.8
- Coreference chains: 0.9

Interpreting the scores depends on the complexity of your type system, the amount and complexity of the content annotated, how experienced the human annotators are, and other factors. For example, if the annotation task is focused on labeling parts of speech, you might expect to see a high score because of how well-defined the parts of speech are. But a task that requires deeper analysis of the text, where human interpretation is required, might show lower scores until you take steps to clarify the causes of the ambiguity.

Generally, a type system that includes many entity types and relation types is open to more interpretation, thus inter-annotator agreement might be lower during the early phases of annotator component development. Looking at the scores, you can see which entity types, for example, have low scores. These low scores are an indication that the annotation guidelines need to be improved. By looking at the scores between pairs of human annotators, you can identify whether a particular annotator consistently shows lower scores than others. This annotator might be having problems understanding the guidelines or using the annotation tools, and thus is a candidate for additional training.

## Reviewing inter-annotator agreement scores
{: #wks_haaccuracy}

When determining which documents are to be promoted to ground truth, you must review the inter-annotator agreement scores. Documents with low scores are candidates to be rejected and returned to the human annotator for improvement.

### About this task

When you examine inter-annotator agreement, you examine documents that were annotated by more than one human annotator. If a document is not shared across multiple annotation sets and human annotators, there is no inter-annotator agreement to calculate. When you add annotation sets to a task, ensure that the sets that you want to compare contain the same overlapping documents. You can see which documents are in an annotation set by opening the **Documents** page, clicking the **Annotation Sets** tab, and then clicking the names of the sets.

You might experience situations in which no overlapping documents are found. This might happen, for example, if you create annotation sets in two rounds and add them to the same task. Even though the annotation sets were created at about the same time, they don't have any documents in common. For another example, if you create annotation sets with overlapping documents, but add one annotation set per task instead of adding all of the annotation sets to a single task, no overlapping documents will be found and inter-annotator agreement cannot be calculated.

### Procedure

To assess annotation agreement between human annotators:

1. Log in as a {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} administrator or project manager, open the **Human Annotation** page, and open the task that you want to evaluate.
1. Click **Calculate IAA**. The default view shows agreement scores for how consistently pairs of human annotators annotated mentions. The top row shows the overall consistency between each pair of annotators, and the table below shows how consistently a pair of annotators labeled specific mentions in the text.
1. To explore how consistently pairs of human annotators annotated relations and coreferences, select **Relation** or **Coreference** from the first menu.
1. To explore how consistently a pair of human annotators annotated entities, relations, or coreferences in specific overlapping documents, select **Document** in the second menu and then select the pair of annotators that you want to evaluate.
1. After reviewing the scores, you can decide whether you want to approve or reject annotation sets that are in Submitted status. After an annotation set is submitted, a check box is displayed next to its name. Take one of these actions:

    - If the inter-annotator agreement scores are acceptable for an annotation set, select the check box and click **Accept**. Documents that do not overlap with other annotation sets are promoted to ground truth. Documents that do overlap must first be reviewed through adjudication so that conflicts can be resolved.
    - If the inter-annotator agreement scores are not acceptable for a annotation set, select the check box and click **Reject**. The annotation set needs to be revisited by the human annotator to improve the annotations.

## Adjudication
{: #wks_haperform}

If multiple human annotators work on the same document, you'll likely want to resolve inconsistencies between the annotations before promoting the annotations to ground truth. This conflict resolution process is known as adjudication.

When you approve annotation sets that are submitted by human annotators, documents that do not overlap between the annotation sets are promoted to ground truth. Before promoting documents that overlap, you should check the annotations for conflicts. When you find instances of disagreement, you must decide how to resolve the conflict, either by selecting the correct annotation from those applied by the human annotators or by selecting a different annotation to apply.

A document is available for adjudication when at least one of the following conditions is true:

- The project manager approves two or more annotation sets in a task at the same time, and the same document exists in at least two of the annotation sets (an overlapping document).
- The project manager approves another annotation set before documents in the previously approved annotation sets are adjudicated. If you adjudicate a document that overlaps between annotation set A and annotation set B, promote the annotations to ground truth, and then approve another annotation set, C, that has the same document, the annotations in the newly approved document are promoted automatically to ground truth because conflicts no longer exist. Be aware that the annotations promoted in annotation set C override the ground truth established when the overlapping documents in annotation sets A and B were adjudicated. If you approve annotation set C before you promote the annotations in annotation set A and B, the overlapping documents in set C can be checked for conflicts and adjudicated.

The amount of time that you spend adjudicating might lessen over time if you take time to improve the annotation guidelines. By providing examples and clarifying areas that caused confusion, you can help human annotators learn from their mistakes and prevent future conflicts.

Here are a few examples of various ways that human annotators disagree:

- **Mentions**

    - Annotator_1 places a mention on a span of text; Annotator_2 does not.
    - Annotator_1's index begins or ends before or after Annotator_2's (there is a partial overlap or subrange of text).
    - Annotator_1 assigns an entity type that is different from the entity type that Annotator_2 assigned.

- **Relations**

    - Annotator_1 creates a relation between two mentions; Annotator_2 does not.
    - Annotator_1 and Annotator_2 create a relation between the same mentions, but with a different relation type.
    - Annotator_1 and Annotator_2 create a relation between the same mentions, but in the reverse order (rare, because the relation between the first mention and second mention is constrained by the type system).

- **Coreference chains**

    - Annotator_1's version of a coreference chain includes (or excludes) mentions that Annotator_2's coreference chain excludes (or includes). The alignment of entities between Annotator_1 and Annotator_2 becomes a matter of scoring.

## Resolving annotation conflicts
{: #wks_haadjudicate}

Adjudication is a step that allows you to review annotation conflicts in overlapping documents before you promote the annotations to ground truth. You can compare the annotations added by a pair of human annotators, or compare human annotations to the current ground truth.

### Before you begin

Click [this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.youtube.com/watch?v=EbexfsuXxoQ&amp;feature=youtu.be){: new_window} to watch a 3-minute video that illustrates how to adjudicate documents.

### About this task

After human annotators complete their annotation tasks, they must submit their completed annotation sets for review. When you evaluate the inter-annotator agreement scores, you can see how different pairs of annotators annotated the same document. If the inter-annotator agreement score is acceptable, you approve the annotation set. If a document does not overlap across annotation sets in the task, the annotations in the approved document are promoted to ground truth. If a document overlaps across annotation sets, you should adjudicate the document and resolve any annotation conflicts that exist before promoting the annotations to ground truth.

For example, when you adjudicate a document, you might see that one annotator annotated the mention `Barack Obama` with the entity type `PeoplePerson`. Another annotator annotated the same string of text as two mentions, assigning the entity type `Person` to `Barack` and the entity type `Person` to `Obama`. To help ensure proper training of the machine-learning annotator, you should resolve this inconsistency.

{{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} supports the ability to adjudicate between two annotation sets at a time, or between an annotation set and the current ground truth. If a document overlaps across more than two annotation sets, adjudicate the two annotation sets that you have the greatest confidence in (perhaps because you have greater confidence in the human annotators) to determine ground truth for the document. And then adjudicate the rest of the annotation sets based on the results of the initial adjudication.

### Procedure

To view overlapping documents and resolve conflicts:

1. Log in as a {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} administrator or project manager, open the **Human Annotation** page, and then open the task that you want to evaluate.
1. Confirm that at least two annotation sets are in **In conflict** status.
1. Click **Check Overlapping Documents for Conflicts**. The documents that are in conflict are listed.
1. If you want to ignore the conflicts in an overlapping document and promote the annotations to ground truth without adjudicating them, click **Accept**.
1. To start resolving conflicts in an overlapping document, click **Check for Conflicts**.
1. If there are three or more candidates for adjudication, including annotation sets that were annotated through human annotation and the current ground truth, select the two candidates that you want to adjudicate and click **Check for Conflicts**. If only two candidates exist, the adjudication tool starts automatically.

    The adjudication tool shows how many mention, relation, and coreference chain conflicts exist. You must resolve mention conflicts before you move on to resolve conflicts between relations and coreference chains.

1. Click to highlight a sentence that contains conflicts. To make it easier to focus on unresolved conflicts, you might want to clear the **Resolved** check box and ensure that the **Unresolved** check box is selected.
1. Click individual annotations and then click **Accept** or **Reject**. To undo a decision that you just made, press **Ctrl+Z**.

    You can also click more than one annotation, and then click to accept or reject all of the selected annotations. If you decide that you want to deselect an annotation that you selected, clear your selections by clicking blank space between sentences or by pressing the **Esc** key.

    If annotation guidelines were previously connected to the project, and you want help with choosing the correct annotation to apply, click **View Guidelines**. Depending on the access permissions set up on the site where the guidelines are hosted, you might be able to update the guidelines after you open them, for example, to add clarifications and examples.
    {: tip}

1. To apply a different entity type to a mention, reject the current annotation, select the mention, such as `Barack Obama`, and then select the correct entity type, such as `Person`.
1. Continue accepting, rejecting, and revising other conflicts in the sentence. After you resolve all conflicts in a sentence, click the **Select all annotations** link and then click **Accept**.
1. Click the arrow icon to go to the next sentence. Continue until all mention conflicts in the document are resolved.

    To save your work in progress, or to temporarily suspend the current adjudication session, click **Save** at any time. If you want to discard all changes that you made, click **Discard**. If you saved the previous adjudication session, and you are ready to resume adjudication, click **Resume** to start adjudicating conflicts where you last stopped. If you discarded the previous adjudication session, you must start a new adjudication session.
    {: tip}

1. After resolving mention conflicts, switch the adjudication mode to resolve any conflicts that occur between relation annotations and coreference chain annotations.

    - Resolving conflicts in relation mode is similar to how you resolve conflicts for mentions. You resolve conflicts on a sentence-by-sentence basis.
    - Coreference chains can exist across multiple sentences. When you move to coreference mode, the system lists the coreference chains that were created by each human annotator in a pane on the right. Select the chains that you want to adjudicate and then click **Reject Chain** or **Accept Chain** to reject or accept annotations in a chain, or click **Merge Chains** to merge the two chains. If you want to remove a mention from a coreference chain, click the delete icon (-) in the label above the mention in the document area.

1. After all conflicts in the document are resolved, click **Promote to Ground Truth**.
