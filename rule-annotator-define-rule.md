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

# Defining a rule
{: #wks_rule_creation}

Use the Rule editor to define rules.
{: shortdesc}

## About this task

Avoid simultaneous editing of rules, classes, and regular expressions by multiple users because it might result in unexpected overwrites or duplication.

## Procedure

To define a rule, complete the following steps:

1. Log in as a {{site.data.keyword.watson}} {{site.data.keyword.knowledgestudioshort}} administrator or project manager and open the **Rules** page.
1. Click the plus sign (+) next to Documents to add a document.

    See [Adding documents for defining rules](/docs/services/knowledge-studio/rule-annotator-add-doc.html) for details.

    For example, you might add a document named My document that contains this single line of text:

    ```
    A 50-year-old driver was driving the 2017 Example Horizon.
    ```
    {: screen}

1. If you plan to define a regular expression or add a dictionary, create a class to associate with it.

    1. From the **Class** side panel, click the plus sign (+) next to Class.
    1. Add a class name.

        If you will associate the class with a regular expression or dictionary, consider naming the class such that you can identify its origin. For example, if you plan to use a regular expression to define a pattern for the number in the sentence, you can create a class named AGE_REGEX. And if you plan to use a dictionary to annotate the car manufacturer in the sentence, you can add a class named MANUFACTURER_DICT.

        Keep these naming rules in mind:
        - The first character in a class name must be alphabetical.
        - Use only the following alphanumeric ASCII characters and the underscore character in values that you add to the classes: A through Z, a through z, 0 through 9.
        - Names cannot contain spaces.
        - Names cannot be longer than 64 characters.

1. Optional: To quickly annotate classes in the document, you can associate a dictionary with the rule editor. Terms in the document that match entries in the dictionary are automatically annotated with the appropriate class.

    1. Click the **Dictionaries** tab in the side panel.

        Any dictionaries that you created are displayed.

        If you have not added a dictionary, open the **Dictionaries** tab from the main navigation bar to add one. See [Creating dictionaries](/docs/services/knowledge-studio/dictionaries.html) for more information.

    1. Click a dictionary, and define a class association for it, and then click **Save**.

        For example, if you have a dictionary that contains organization names, you can associate it with the rule and assign the ORGANIZATION_DICT class to it. Any organization names that occur in your sample documents will be annotated as instances of the ORGANIZATION_DICT class.

    If you want to remove the dictionary association from the rule editor later, then you can remove the class mapping. To do so, choose the empty option from the top of the drop-down list.

1. Optional: To define a regular expression to help you construct a rule, click the **Regex** tab in the side panel.

    1. Click the plus sign (+) next to Regular Expressions to add a regular expression.
    1. Name the regular expression. For example, MyAgeRegex.

        The name cannot be longer than 64 characters.

    1. Associate the expression with a class. For example, AGE_REGEX.
    1. Click **Add Entry**.
    1. Add the expression.

        For example, to capture a number that represents an age (up to age 99), you can specify `[0-9]{1,2}`. To capture expressions of time, like *12:30 AM*, you might specify this regular expression:

        ```
        (1[0-2]|0?[1-9]):([0-5][0-9])(\s+[AaPp][Mm])?
        ```
        {: screen}

        You can optionally change the minimum and maximum number of word tokens. In English, tokens are often equated to words as delimited by white spaces in a sentence. However, they do not always match one-to-one with words; other textual elements are considered tokens in some situations. For example, the hyphens in the term *50-year-old* each count as a token, which means the total number of tokens used in this term is 5. And the text *12:30 PM* contains 4 tokens. (`12 | : | 30 | PM`)

        Click **Add**.

    1. Repeat the previous two steps if you want to add more expressions.
    1. Click **Save**.

    The Regex editor closes, and the document is displayed. You should see the class that you defined for the regular expression applied to the text that you intended it to match against. If you do not, check your expression. It might need to be revised so it matches the text that you intended for it to find.

    ![The rule editor showing the "Regex" tab selected, a regular expression called "Age" that's associated with the class "AGE_REGEX", and a document that shows the text "50" highlighted in yellow. The highlighted text matches the regular expression that was created.](images/rule_step3.jpg)

1. To define a rule, click the **Rules** tab in the side panel.
1. Click to open the document with the pattern that you want to capture as a rule.
1. From the text in the document, select the words that illustrate the pattern that you want to capture. Click the plus sign (+) in the **Rules** side panel. For example, you might select the text:

    ```
    50-year-old
    ```
    {: screen}

    The rule editor represents the text that you selected as two layers of cells. The cells in the top layer are where you annotate the classes of the underlying tokens. The lower layer is where you define the conditions by which the tokens participate in the pattern.

    ![The rule editor that shows what the "Rules" tab looks like after you select text from your document and click the plus sign in the "Rules" side panel. The following graphical elements are shown: the "Rule name" field with the term "AGE" entered, the "Create a rule" panel, and the "Class" side panel. In the "Create a rule" panel, cells with dotted lines are shown across the top. One cell is shown for each token of the text that was selected. In these cells, you annotate the classes of the tokens. Across the bottom of the "Create a rule" panel, cells with solid lines are shown. Each cell contains a token of the selected text, "50-year-old". The tokens are "50", "-" (hyphen), "year", "-", and "old". Each solid-line cell has two icons next to it that you can use to adjust the condition of the word or annotation.](images/rule_step4.jpg)

1. Start by defining the conditions by which the token participates in the pattern.

    In the bottom layer of cells, click the first token to review its conditions. If you want to indicate that any token can be used in the current position in the pattern, then click **Open Properties**, and check **Any token**. Click **Close Properties**.

    > **Note:** The maximum number of single token, annotation, or 'any token' group cells that can participate in a pattern is 15 when each cell has a repeat setting of 1 or less. And the maximum number of total tokens allowed in a pattern is 20. Take the repeat setting of each cell into account as you define the pattern. For example, you can define a pattern that includes 15 tokens when each cell has a repeat setting of 1 or less. But, you can define no more than 4 tokens in the pattern if each one has a repeat setting of 1 or more because for each one, the token can repeat up to 5 times. 4 tokens repeated 5 times brings you to the allowed maximum of 20.

    To indicate that a particular type of token is required, you can define the following types of condition settings:
    - **Repeat Setting**: Specifies how many times the current token must be included in the pattern. You can change the repeat setting, but only one repeat setting can be specified per token. The options are described in the following table.

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e471" class="stentry thleft thbot">Setting Option</th>
        <th valign="bottom" align="left" id="d27028e473" class="stentry thleft thbot">Description</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Required (Exactly 1)</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">This token must exist in the pattern
            one time. This option is applied by default, but can
            be changed.</p></td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Repeating 1 or more times</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">This token must exist in the pattern
            at least one time, and can repeat more times.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Repeating 0 or more times</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">This token can optionally repeat in
            the pattern many times, but does not have to repeat.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Occurring 0 or 1 time</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">This token is optional.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e471" class="stentry">
          <p class="p wrapper">Advanced: &lt;custom&gt;</p>
        </td>
        <td valign="top" headers="d27028e473" class="stentry">
          <p class="p wrapper">This token must repeat in the pattern
            the number of times that is specified here. To define
            a custom repeat setting, click
            <b>Open Properties</b>,
            select the Advanced option, and then you can change
            the numbers.</p>
          <p class="note">
            The maximum number of repeats allowed for a token is
            5.</p>
        </td>
      </tr>
    </table>

    - **Feature Setting**: At least one of the feature settings must be defined. You can add more features to add to the number of conditions that must be met for text to match this pattern. The options are described in the following table.

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e512" class="stentry thleft thbot">Setting Option</th>
        <th valign="bottom" align="left" id="d27028e514" class="stentry thleft thbot">Condition it adds</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e512" class="stentry">
          <p class="p wrapper">Text</p>
        </td>
        <td valign="top" headers="d27028e514" class="stentry">
          <p class="p wrapper">Must match the exact text in this
            token. This option is applied by default. You can remove
            it, but only if you add a different setting as a condition
            or apply the Any token setting.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e512" class="stentry">
          <p class="p wrapper">Length</p>
        </td>
        <td valign="top" headers="d27028e514" class="stentry">
          <p class="p wrapper">Must match the character length of
            this token. The length is counted starting at 0 from in
            front of the first character.</p>
        </td>
      </tr>
    </table>

    The rest of the options differ depending on the type of the token.

    - **Unannotated token that does not match a regex or dictionary term**: These settings are available for tokens that are not annotated and do not match a regex or dictionary term.

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e535" class="stentry thleft thbot">Setting Option</th>
        <th valign="bottom" align="left" id="d27028e537" class="stentry thleft thbot">Description</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">Part of speech</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">Must be the same part of speech
            as this token. The following types are supported:</p>
          <ul class="ul bullets">
            <li class="li">
              <p class="p wrapper">adjective</p>
            </li>
            <li class="li">
              <p class="p wrapper">adposition</p>
            </li>
            <li class="li">
              <p class="p wrapper">adverb</p>
            </li>
            <li class="li">
              <p class="p wrapper">conjunction</p>
            </li>
            <li class="li">
              <p class="p wrapper">determiner</p>
            </li>
            <li class="li">
              <p class="p wrapper">interjection</p>
            </li>
            <li class="li">
              <p class="p wrapper">noun</p>
            </li>
            <li class="li">
              <p class="p wrapper">numeral</p>
            </li>
            <li class="li">
              <p class="p wrapper">pronoun</p>
            </li>
            <li class="li">
              <p class="p wrapper">residual</p>
            </li>
            <li class="li">
              <p class="p wrapper">verb </p>
            </li>
          </ul>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">Lemma</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">Must have the same lemma as this
            token.</p>
        </td>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e535" class="stentry">
          <p class="p wrapper">Character Type</p>
        </td>
        <td valign="top" headers="d27028e537" class="stentry">
          <p class="p wrapper">Must have the same character type
            as this token. The following types are supported:</p>
          <ul class="ul bullets">
            <li class="li">
              <p class="p wrapper">Arabic: Contains a sequence
                of Arabic characters</p>
            </li>
            <li class="li">
              <p class="p wrapper">ChineseNumeral: Contains only
                Chinese numerals</p>
            </li>
            <li class="li">
              <p class="p wrapper">ClauseEndingPunctuation:
                Punctuation characters that separate one clause
                or sentence from the next</p>
            </li>
            <li class="li">
              <p class="p wrapper">Han: Contains Han characters</p>
            </li>
            <li class="li">
              <p class="p wrapper">Hangul: Contains Korean Hangul
                syllabic characters</p>
            </li>
            <li class="li">
              <p class="p wrapper">Hebrew: Contains a sequence of
                Hebrew characters</p>
            </li>
            <li class="li">
              <p class="p wrapper">Hiragana: Contains Japanese
                Hiragana syllabic characters</p>
            </li>
            <li class="li">
              <p class="p wrapper">Ideographic: Contains an
                ideogram, or symbol representing an idea or
                thing</p>
            </li>
            <li class="li">
              <p class="p wrapper">Katakana: Contains Japanese
                Katakana syllabic characters</p>
            </li>
            <li class="li">
              <p class="p wrapper">Lowercase: Contains only lower
                case alphabetic characters</p>
            </li>
            <li class="li">
              <p class="p wrapper">Numeric: Contains only numeric
                characters</p>
            </li>
            <li class="li">
              <p class="p wrapper">Punctuation: One or more
                characters that provide punctuation in the
                text</p>
            </li>
            <li class="li">
              <p class="p wrapper">Syllabic: Contains syllabic
                characters</p>
            </li>
            <li class="li">
              <p class="p wrapper">Thai: Contains Thai
                characters</p>
            </li>
            <li class="li">
              <p class="p wrapper">Titlecase: Starts with a
                single upper case alphabetic character, followed
                by one or more lower case alphabetic characters</p>
            </li>
            <li class="li">
              <p class="p wrapper">Uppercase: A token containing
                only upper case alphabetic characters</p>
            </li>
          </ul>
        </td>
      </tr>
    </table>

    - **Rule Match:**

    <table cellpadding="4" cellspacing="0" summary="" border="1" class="simpletable">
      <tr class="sthead">
        <th valign="bottom" align="left" id="d27028e617" class="stentry thleft thbot">Setting Option</th>
        <th valign="bottom" align="left" id="d27028e619" class="stentry thleft thbot">Description</th>
      </tr>
      <tr class="strow">
        <td valign="top" headers="d27028e617" class="stentry">
          <p class="p wrapper">Rule Match</p>
        </td>
        <td valign="top" headers="d27028e619" class="stentry">
          <p class="p wrapper">Must match the named class.
            Remember, a class can be derived from a regex,
            a dictionary, or a rule. If the class specified
            here was derived from a regular expression, for
            example, then this token must match the search
            pattern of the expression.</p>
        </td>
      </tr>
    </table>

1. For tokens that have annotations (that were added indirectly from a dictionary annotation or regular expression match), you can choose whether the pattern should require any word with the same annotation type or the actual underlying words that were annotated instead.

    In the lower layer of cells, you can see which cells are included in the pattern because a horizontal line connects them to one another. Where an annotation has been applied, there is a split. Cells with the original words are displayed below a cell with the annotation label. You can click one set of cells or the other to change the path of the line, and thus change the cells that are included in the pattern.

    For example, you could choose to have the pattern use 50 instead of having it match the age regular expression.

    ![The "Create a rule" panel that shows an edit of the token, "50", that uses the annotation, "AGE_REGEX", in the rule. By default, the "AGE_REGEX" annotation is used, but you can edit the pattern so that the underlying word, "50", is used instead.](images/rule_step5.jpg)

1. After you set the pattern order, you can annotate tokens in the text.

    From the top layer of cells, click the cells that represents the tokens that you want to annotate, and then apply a class label to them. To select multiple cells, click one, press the **Shift** key, and click additional cells.

    Assign a class to the selected cell or cells. If the class you want to assign does not exist, you can add it. Type the class name into the **Assign class** field and press **Enter**.

    > **Note:** You cannot add more than 10 classes for the rule.

    ![The "Create a rule" section showing the "Assign class" window that opens when you click a token. The window shows a field where you can enter the name of a new class, or select an existing class from the list.](images/rule_step6.jpg)

1. Name the rule.

    The rule name cannot be longer than 64 characters.

1. Click **Save** in the Rules side panel to save the rule.
