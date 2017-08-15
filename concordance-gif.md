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

# How to use the concordance tool
{: #concordance-gif}

This graphic illustrates how to use the concordance tool to find all mentions of the ORGANIZATION entity, *Microsoft*.
{: shortdesc}

![Shows the user starting the concordance tool, and then selecting Microsoft. When prompted, the user chooses to preview, and then apply and review the mentions. She removes the Microsoft reference that is part of the word Microsoft Corp. but applies the ORGANIZATION entity type to all of the other mentions that are found by the tool.](images/concordance1.gif)

It is not shown here, but during the preview process, you have a chance to remove proposed annotations that you do not want to apply to the document. For example, note that the mention of *Microsoft Corp.* that occurs in this document is not annotated by the concordance tool. The concordance tool did propose the addition of an entity mention for the substing *Microsoft* in *Microsoft Corp.*, but during the review process, the user removed it from the list. The full reference *Microsoft Corp.* is annotated separately. Separately, you can teach the machine-learning annotator that the *Microsoft* and *Microsoft Corp.* mentions refer to the same entity by using a coreference chain to associate them with one another.

## Related tasks

[Annotating repeating mentions](/docs/services/knowledge-studio/user-guide.html#wks_haconcordance)
