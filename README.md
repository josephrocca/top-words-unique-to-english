# top-words-unique-to-english
Top 4000+ words that are (spelling-wise) unique to English

https://github.com/oprogramador/most-common-words-by-language

```js
let text = await fetch("https://raw.githubusercontent.com/oprogramador/most-common-words-by-language/master/src/resources/english.txt").then(r => r.text());
let englishWords = new Set(text.split("\n").map(w => w.trim().toLowerCase()));

let otherLanguages = ["afrikaans","albanian","arabic","bengali","bulgarian","catalan","chinese","czech","danish","dutch","esperanto","estonian","farsi","finnish","french","german","greek","hebrew","hindi","hungarian","indonesian","italian","japanese","kazakh","korean","latvian","lithuanian","macedonian","norwegian","polish","portuguese","romanian","russian","serbian","slovak","slovenian","spanish","swedish","thai","turkish","ukrainian","vietnamese"];
for(let language of otherLanguages) {
  let text = await fetch(`https://raw.githubusercontent.com/oprogramador/most-common-words-by-language/master/src/resources/${language}.txt`).then(r => r.text());
  let words = new Set(text.split("\n").map(w => w.trim().toLowerCase()));
  for(let word of words) {
    englishWords.delete(word);
  }
}
console.log([...englishWords].join("\n"));
```
