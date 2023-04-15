# JMdict for Yomichan

This simply contains various versions of JMdict Yomichan dictionaries
from the [main website](https://www.edrdg.org/wiki/index.php/JMdict-EDICT_Dictionary_Project)
(from files `JMdict_e` and `JMdict_e_examp`),
compiled using [yomichan-import](https://github.com/FooSoft/yomichan-import).
(Disclaimer: I did not make any of these tools.)

This repository exists to simply give people a more up-to-date version of this dictionary,
for people who don't want to compile the dictionary themselves.
A more up-to-date version of JMdict usually provides better definitions and coverage
compared to older versions, so I would recommend updating this dictionary every few months.

[**(DOWNLOAD UNDER RELEASES)**](https://github.com/Aquafina-water-bottle/jmdict-english-yomichan/releases)

To see your current version of JMdict,
hover over this entry:
> ＪＭｄｉｃｔ

## JMdict (English)
For JMdict English users, there are a few versions available:

* `jmdict_english`: The default version.
* `jmdict_english_extra`: Contains a lot of extra information not included in the default version,
    including alternate forms and antonyms
* `jmdict_english_extra_with_examples`: Contains the above and extra sentences.
    **You likely want to be using this one**.

> **Note**: The extra versions will take considerably longer to import compared to the default version.

<!--
Additionally, as of writing this (2022/09/20),
all of the following sources provide relatively older versions of JMdict:
- Matt's Yomichan video (Exact version not included, but likely before 2021)
- Yomichan README (2021-01-01)
In the future, I plan on writing something to automatically re-compile this dictionary daily / weekly.
-->

## "JMdict English Extra" Usage Notes
* For Windows users with a Chromium based browser (i.e. Google Chrome, Opera, Microsoft Edge, etc.),
    some emojis will not properly show (i.e. the flags).
    You can instead customize the emojis using the following CSS
    [(relevant github issue)](https://github.com/FooSoft/yomichan-import/pull/40#issuecomment-1426941717):

    <details>
    <summary> Sample CSS <i>(click here)</i> </summary>

    ```css
    ul[data-sc-content="glossary"] {
      list-style-type: circle !important;
    }
    ul[data-sc-content="infoGlossary"] {
      list-style-type: "ℹ️ " !important; /* hint: try "💬 " */
    }
    ul[data-sc-content="sourceLanguages"] {
      list-style-type: "🌐 " !important;
    }
    ul[data-sc-content="notes"] {
      list-style-type: "📝 " !important;
    }
    ul[data-sc-content="antonyms"] {
      list-style-type: "🔄 " !important;
    }
    ul[data-sc-content="references"] {
      list-style-type: "➡️ " !important;
    }
    ul[data-sc-content="examples"] {
      list-style-type: "🇯🇵 " !important; /* hint: try "⛩️ ", "👺 ", "🗾 ", or "🎌 " */
    }
    ul[data-sc-content="examples"] > li[lang="en"] {
      list-style-type: "🇬🇧 " !important; /* hint: try "🗽 ", or "🌎 " */
    }
    ```

    </details>

    <details>
    <summary> Sample CSS (Text only, no emojis) </summary>

    ```css
    ul[data-sc-content="glossary"] {
      list-style-type: circle !important;
    }
    ul[data-sc-content="infoGlossary"] {
      list-style-type: "◆ " !important; /* matches closer with monolingual dictionaries. If you want a symbol, try "ⓘ  " */
    }
    ul[data-sc-content="sourceLanguages"] {
      list-style-type: "語源: " !important;
    }
    ul[data-sc-content="notes"] {
      list-style-type: "メモ: " !important;
    }
    ul[data-sc-content="antonyms"] {
      list-style-type: "⇔  " !important;
    }
    ul[data-sc-content="references"] {
      list-style-type: "↪  " !important;
    }
    ul[data-sc-content="examples"] {
      list-style-type: "例文: " !important;
    }

    ol[data-count="1"].definition-list ul[data-sc-content="examples"],
    ol[data-count="1"].definition-list ul[data-sc-content="references"],
    ol[data-count="1"].definition-list ul[data-sc-content="antonyms"],
    ol[data-count="1"].definition-list ul[data-sc-content="notes"],
    ol[data-count="1"].definition-list ul[data-sc-content="sourceLanguages"],
    ol[data-count="1"].definition-list ul[data-sc-content="infoGlossary"] {
      padding-left: 2em !important;
    }
    ```

    </details>

    The CSS above will not affect exported Anki definitions. You will need to add the appropriate CSS to your card template,
    if you want to change it for Anki as well.

* Exporting cards with compact mode will [not export correctly](https://github.com/FooSoft/yomichan/issues/2297).
    In order to fix this, your main solution is to add the following CSS as described [here](https://github.com/FooSoft/yomichan/issues/2297#issuecomment-1426828952):
    ```css
    ul[data-sc-content="glossary"] li {
      display: inline-block;
      padding-right: 1em;
      margin-right: 1em;
      border-right: 2px solid;
    }

    ul[data-sc-content="glossary"] li:last-of-type {
      padding-right: 0px;
      margin-right: 0px;
      border-right: 0px solid;
    }
    ```

    If you prefer plaintext definitions, see options 1. and 2. as listed [here](https://github.com/FooSoft/yomichan/issues/2297#issuecomment-1435371920).
    I highly recommend contributing a proper solution to Yomichan if you're interested.

