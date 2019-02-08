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

This documentation is for {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.IBM}} Marketplace. To see the documentation for the new version of {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.cloud_notm}}, [click this link ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/docs/services/watson-knowledge-studio/language-support-arabic.html){: new_window}.
{: tip}

# Configuring support for Arabic
{: #wks_langsupp_ar}

Read these guidelines to understand how {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} handles Arabic character shaping and numeric shaping in Arabic documents.

## About this task

With respect to character shaping, the Arabic alphabet does not have capital letters, but letters can change shape depending on their position in the text string and the surrounding letters. Different operating systems and code page conversion programs handle letter shaping in different ways. Unshaped storage is a standard for Windows systems, and {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} presumes that Arabic text is stored unshaped. If you want to import shaped text into {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} , you must first convert the text to unshaped form by using standard tools, such as the International Components for Unicode (ICU) API (see the ArabicShaping Class at [http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://icu-project.org/apiref/icu4j/com/ibm/icu/text/ArabicShaping.html){: new_window}).

> **Important:** In some cases, lack of proper Arabic character shaping might cause content to be displayed incorrectly in the Ground Truth Editor.

With respect to numeric shaping, {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} treats numeric shaping as a storage-level property, similar to how Arabic content is handled on the iOS platform. Because a lot of Arabic content is created on platforms like Windows, which treat numeric shaping as a display-level property, you need to either convert content to make numeric shaping a storage-level property or use a Firefox browser when you use {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}}. Firefox supports the ability to set numeric shaping preferences explicitly at the browser level and enforce the appropriate display for all content shown in the browser.

## Procedure

To configure numeric shaping in the Firefox browser:

1. In the browser URL field, enter **about:config**. If you are shown a warning from Firefox, click the action to disregard the warning and continue. For information about editing **about:config** properties, see [http://kb.mozillazine.org/About:config_entries ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://kb.mozillazine.org/About:config_entries){: new_window}.
1. Type `bidi` in the search filter field.
1. Select the **bidi.numeral** property, which controls how numerals are displayed, and press Enter.
1. Change the value of this property as required. For example, enter `3` and then click **OK**.

    - **0**: Nominal numerals (the default value)
    - **1**: Regular context numerals
    - **2**: Hindi context numerals
    - **3**: Arabic numerals
    - **4**: Hindi numerals

    > **Important:** When the **bidi.numeral** property is used, Firefox completely ignores the code point of specific digit characters in the content of a web page.

### Related reference

[Multiple language support](/docs/services/knowledge-studio/language-support.html)
