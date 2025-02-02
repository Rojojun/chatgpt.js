<div align="center">

<div align="right">

######  Italiano | <a href="../..#readme">English</a> | <a href="../zh-cn#readme">简体中文</a> | <a href="../ja#readme">日本</a> | <a href="../hi#readme">हिंदी</a> | <a href="../de#readme">Deutsch</a> | <a href="../es#readme">Español</a> | <a href="../fr#readme">Français</a> | <a href="../pt#readme">Português</a>

</div>

<br>

<h3>

<picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/kudoai/chatgpt.js/main/media/images/chatgpt.js-logo-dark-mode-5995x619.png">
    <img width=700 src="https://raw.githubusercontent.com/kudoai/chatgpt.js/main/media/images/chatgpt.js-logo-light-mode-5995x619.png">
</picture>
<br><br>

🤖 Eine leistungsstarke clientseitige JavaScript-Bibliothek für ChatGPT
<br><br>

</div>
</h3>

<div align="center">

[![](https://img.shields.io/badge/Licenza-MIT-green.svg?logo=internetarchive&logoColor=white&labelColor=464646&style=for-the-badge)](LICENSE.md)
[![](https://img.shields.io/github/commit-activity/m/kudoai/chatgpt.js?label=Commette&logo=github&logoColor=white&labelColor=464646&style=for-the-badge)](https://github.com/kudoai/chatgpt.js/commits/main)
![](https://img.shields.io/github/size/kudoai/chatgpt.js/dist/chatgpt-1.12.0.min.js?label=Dimensione+Minimizzata&logo=databricks&logoColor=white&labelColor=464646&color=ff69b4&style=for-the-badge)
[![](https://img.shields.io/codefactor/grade/github/kudoai/chatgpt.js?label=Qualità+del+Codice&logo=codefactor&logoColor=white&labelColor=464646&style=for-the-badge)](https://www.codefactor.io/repository/github/kudoai/chatgpt.js)
[![](https://img.shields.io/badge/Menzionato_in-Awesome-cca8c4?logo=awesomelists&logoColor=white&labelColor=464646&style=for-the-badge)](https://github.com/sindresorhus/awesome-chatgpt#javascript)
[![](https://img.shields.io/badge/In_Evidenza-Product_Hunt-ff6154?logo=producthunt&logoColor=white&labelColor=464646&style=for-the-badge)](https://www.producthunt.com/posts/chatgpt-js)
![](https://img.shields.io/jsdelivr/gh/hw/kudoai/chatgpt.js?label=jsDelivr+Colpi&logo=jsdelivr&logoColor=white&labelColor=464646&color=gold&style=for-the-badge)

</div>

## Di

**chatgpt.js** è una potente libreria JavaScript che consente un'interazione semplicissima con ChatGPT DOM.

- Ricco di funzionalità
- Orientato agli oggetti
- Facile da usare
- Leggero (ma ottimamente performante)

<p><img type="separator" height=8px width="100%" src="https://raw.githubusercontent.com/kudoai/chatgpt.js/main/media/images/separators/aqua.png"></p>

## ⚡ Importazione della libreria

### ES6:

```js
(async () => {
  await import('https://code.chatgptjs.org/chatgpt-latest.min.js');
  // Il tuo codice qui...
})();
```

### ES5:

```js
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://code.chatgptjs.org/chatgpt-latest.min.js');
xhr.onload = function () {
  if (xhr.status === 200) {
    var chatgptJS = document.createElement('script');
    chatgptJS.textContent = xhr.responseText;
    document.head.appendChild(chatgptJS);
    yourCode(); // esegue il tuo codice
  }
};
xhr.send();

function yourCode() {
  // Il tuo codice qui...
}
```

### <img style="margin: 0 2px -0.065rem 0" height=17 src="https://i.imgur.com/SATGr8j.png"></picture><img style="margin: 0 2px -0.035rem 1px" height=17.5 src="https://i.imgur.com/wcCg3al.png"> Greasemonkey:

> **Nota** _Per utilizzare un modello iniziale: [kudoai/chatgpt.js-greasemonkey-starter](https://github.com/kudoai/chatgpt.js-greasemonkey-starter)_

I repository di Userscript come Greasy Fork mantengono una whitelist di CDN pre-approvati (come i riferimenti specifici del commit da `cdn.jsdelivr.net`) quindi l'URL di importazione è sostanzialmente più lungo per preservare la pubblicabilità su questi siti:

```js
...
// @require https://cdn.jsdelivr.net/gh/kudoai/chatgpt.js@24a755998291094d0cd3b2bd395dff7c6756bbf9/dist/chatgpt-1.12.0.min.js
// ==/UserScript==

// Il tuo codice qui...
```

Se non hai intenzione di pubblicare su questi repository, puoi utilizzare il più semplice `https://code.chatgptjs.org/chatgpt-latest.min.js` per importare l'ultima versione minimizzata.

### <img style="margin: 0 2px -1px 0" height=16 src="https://www.google.com/chrome/static/images/favicons/apple-icon-60x60.png"> Chrome:

> **Nota** _Per utilizzare un modello iniziale: [kudoai/chatgpt.js-chrome-starter](https://github.com/kudoai/chatgpt.js-chrome-starter)_

Poiché Google [alla fine eliminerà gradualmente](https://developer.chrome.com/docs/extensions/migrating/mv2-sunset/) Manifest V2, il codice remoto non sarà più consentito, quindi l'importazione locale di chatgpt.js è l'ideale:

1. Salva https://raw.githubusercontent.com/kudoai/chatgpt.js/main/chatgpt.js in una sottodirectory (`lib` in questo esempio)

2. Aggiungi la dichiarazione di esportazione ES6 alla fine di `lib/chatgpt.js`
```js
...
export { chatgpt }
```

3. In `manifest.json` del progetto (V3), aggiungi `lib/chatgpt.js` come risorsa accessibile dal web
```json
    "web_accessible_resources": [{
        "matches": ["<all_urls>"],
        "resources": ["lib/chatgpt.js"]
    }],
```

4. Negli script che richiedono `chatgpt.js` (in primo piano/sfondo allo stesso modo), importalo in questo modo:
```js
(async () => {
  const { chatgpt } = await import(chrome.runtime.getURL('lib/chatgpt.js'));
  // Il tuo codice qui...
})();
```

<p><img type="separator" height=8px width="100%" src="https://raw.githubusercontent.com/kudoai/chatgpt.js/main/media/images/separators/aqua.png"></p>

## 💻 Utilizzo

**chatgpt.js** è stato scritto pensando all'estrema flessibilità.

Per esempio:

```js
chatgpt.getLastResponse();
chatgpt.getLastReply();
chatgpt.response.getLast();
chatgpt.get('reply', 'last');
```

Ogni chiamata recupera ugualmente l'ultima risposta. Se pensi che funzioni, probabilmente lo farà... quindi digitalo!

In caso contrario, invia semplicemente un [problema](https://github.com/kudoai/chatgpt.js/issues) o [PR](https://github.com/kudoai/chatgpt.js/pulls) e sarà integrato, vai tranquillo!

<p><img type="separator" height=8px width="100%" src="https://raw.githubusercontent.com/kudoai/chatgpt.js/main/media/images/separators/aqua.png"></p>

## 🤖 Realizzato con chatgpt.js

### <picture><source media="(prefers-color-scheme: dark)" srcset="https://i.imgur.com/RduASbD.png"><img width=16 src="https://raw.githubusercontent.com/adamlui/chatgpt-addons/main/media/icons/openai-favicon64.png"></picture> [Cancella Cronologia ChatGPT](https://chatgptevo.com/autoclear) <a href="https://github.com/awesome-scripts/awesome-userscripts#chatgpt"><img src="https://awesome.re/mentioned-badge.svg" style="margin:0 0 -2px 5px"></a>

Cancella automaticamente la cronologia delle query ChatGPT per la massima privacy.
<br>[Installare](https://github.com/adamlui/autoclear-chatgpt-history#installation) /
[Leggimi](https://github.com/adamlui/autoclear-chatgpt-history#readme) /
[Discutere](https://github.com/adamlui/autoclear-chatgpt-history/discussions)

### <img width=16 src="https://i.imgur.com/1yjmK3W.png"> [Automatic ChatGPT DAN](https://github.com/madkarmaa/automatic-chatgpt-dan)

Invia automaticamente richieste DAN a ChatGPT.
<br>[Installare](https://github.com/madkarmaa/automatic-chatgpt-dan#%EF%B8%8F-installation) /
[Leggimi](https://github.com/madkarmaa/automatic-chatgpt-dan#readme) /
[Discutere](https://github.com/madkarmaa/automatic-chatgpt-dan/issues)

### <img src="https://media.bravegpt.com/images/bravegpt-icon48.png" width=18> [BraveGPT](https://bravegpt.com) <a href="https://www.producthunt.com/posts/bravegpt?utm_source=badge-featured&utm_medium=badge&utm_souce=badge-bravegpt" target="_blank"><img src="https://api.producthunt.com/widgets/embed-image/v1/featured.svg?post_id=385630&theme=light" style="width: 112px; height: 24px; margin:0 0 -4px 5px;" width="112" height="24" /></a>

Mostra le risposte di ChatGPT nella barra laterale di Brave Search (basata su GPT-4!)
<br>[Installare](https://github.bravegpt.com/#installation) /
[Leggimi](https://github.bravegpt.com/#readme) /
[Discutere](https://github.bravegpt.com/discussions)

### <picture><source media="(prefers-color-scheme: dark)" srcset="https://i.imgur.com/RduASbD.png"><img width=16 src="https://raw.githubusercontent.com/adamlui/chatgpt-userscripts/main/media/icons/openai-favicon64.png"></picture> [ChatGPT Auto-Continua ⏩](https://chatgptevo.com/autocontinue/github) <a href="https://github.com/awesome-scripts/awesome-userscripts#chatgpt"><img src="https://awesome.re/mentioned-badge.svg" style="margin:0 0 -3px 3px"></a>

Continua automaticamente a generare più risposte di ChatGPT.<br>
[Installare](https://github.com/adamlui/chatgpt-auto-continue#installation) /
[Leggimi](https://github.com/adamlui/chatgpt-auto-continue#readme) /
[Discutere](https://chatgptevo.com/autocontinue/discussions)

### <picture><source media="(prefers-color-scheme: dark)" srcset="https://i.imgur.com/RduASbD.png"><img width=16 src="https://raw.githubusercontent.com/adamlui/chatgpt-addons/main/media/icons/openai-favicon64.png"></picture> [ChatGPT Aggiornamento Automatico ↻](https://chatgptevo.com/autorefresh) <a href="https://github.com/awesome-scripts/awesome-userscripts#chatgpt"><img src="https://awesome.re/mentioned-badge.svg" style="margin:0 0 -2px 5px"></a>

Mantiene aggiornate le sessioni ChatGPT per eliminare errori di rete + controlli Cloudflare.
<br>[Installare](https://github.com/adamlui/chatgpt-auto-refresh#installation) /
[Leggimi](https://github.com/adamlui/chatgpt-auto-refresh#readme) /
[Discutere](https://github.com/adamlui/chatgpt-auto-refresh/discussions)

### <img src="https://media.duckduckgpt.com/images/ddgpt-icon48.png" width=17> [DuckDuckGPT](https://duckduckgpt.com) <a href="https://www.producthunt.com/posts/duckduckgpt?utm_source=badge-featured&utm_medium=badge&utm_souce=badge-duckduckgpt" target="_blank"><img src="https://api.producthunt.com/widgets/embed-image/v1/featured.svg?post_id=379261&theme=light" style="width: 112px; height: 24px; margin:0 0 -4px 5px;" width="112" height="24" /></a>

Visualizza le risposte di ChatGPT nella barra laterale di DuckDuckGo (basata su GPT-4!)
<br>[Installare](https://github.duckduckgpt.com/#installation) /
[Leggimi](https://github.duckduckgpt.com/#readme) /
[Discutere](https://github.duckduckgpt.com/discussions)

<br>

<a href="https://chatgptinfinity.com" target="_blank"><img width=555 src="https://raw.githubusercontent.com/adamlui/chatgpt-infinity/main/chrome/media/images/tiles/marquee-promo-tile-1400x560.png"></a>

<br>

<a href="https://chatgptwidescreen.com" target="_blank"><img width=555 src="https://raw.githubusercontent.com/adamlui/chatgpt-widescreen/main/chrome/media/images/tiles/marquee-promo-tile-1400x560.png"></a>

<br>

Se hai creato qualcosa con chatgpt.js che desideri condividere, invia un'email a [showcase@chatgptjs.org](mailto:showcase@chatgptjs.org) o semplicemente apri una [pull request](https://github.com/kudoai/chatgpt.js/pulls)!

<p><img type="separator" height=8px width="100%" src="https://raw.githubusercontent.com/kudoai/chatgpt.js/main/media/images/separators/aqua.png"></p>

## 🧠 Contributori

Questa libreria esiste grazie al codice, alle traduzioni, ai problemi e alle idee dei seguenti contributori:

[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/10906554?first-contrib=2023.03.15&h=50&w=50&mask=circle&maxage=7d '@adamlui')](https://github.com/adamlui)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/71683364?first-contrib=2023.03.16-get-functions&h=50&w=50&mask=circle&maxage=7d '@mefengl')](https://github.com/mefengl)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/131989355?first-contrib=2023.04.30-doc-translations&h=50&w=50&mask=circle&maxage=7d '@Zin6969')](https://github.com/Zin6969)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/30551844?first-contrib=2023.05.02-getlastresponse-bug-report&h=50&w=50&mask=circle&maxage=7d '@madruga8')](https://github.com/madruga8)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/54934866?first-contrib=2023.05.01-clearchats-discard-fix&h=50&w=50&mask=circle&maxage=7d '@XiaoYingYo')](https://github.com/XiaoYingYo)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/129722778?first-contrib=2023.05.24-css-readability&h=50&w=50&mask=circle&maxage=7d '@AliAlSarre')](https://github.com/AliAlSarre)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/100418457?first-contrib=2023.06.02-send-function-bug-report&h=50&w=50&mask=circle&maxage=7d '@madkarmaa')](https://github.com/madkarmaa)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/1170326?first-contrib=2023.06.10-html-parser-idea&h=50&w=50&mask=circle&maxage=7d '@wamoyo')](https://github.com/wamoyo)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/33952?first-contrib=2023.06.10-html-parser-idea&h=50&w=50&mask=circle&maxage=7d '@meiraleal')](https://github.com/meiraleal)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/u/22633385?first-contrib=2023.07.11-fix-ja-doc-md&h=50&w=50&mask=circle&maxage=7d '@eltociear')](https://github.com/eltociear)
[![](https://images.weserv.nl/?url=https://avatars.githubusercontent.com/in/29110&h=50&w=50&mask=circle&maxage=7d 'Dependabot')](https://github.com/dependabot)
[![](https://images.weserv.nl/?url=https://i.imgur.com/tNyIPmG.jpg?h=50&w=50&mask=circle&maxage=7d 'ChatGPT')](https://chat.openai.com)

<br>

<p><img type="separator" height=8px width="100%" src="https://raw.githubusercontent.com/kudoai/chatgpt.js/main/media/images/separators/aqua.png"></p>

<div id="star-history" align="center">

<br>

<a href="https://star-history.com/#kudoai/chatgpt.js&Timeline">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=kudoai/chatgpt.js&type=Timeline&theme=dark" />
    <img width=665 src="https://api.star-history.com/svg?repos=kudoai/chatgpt.js&type=Timeline" />
  </picture>
</a>

<br>_Considera di dare a questo repository un ⭐ se ti ha aiutato!_

</div>

#

<a href="https://github.com/kudoai/chatgpt.js/tree/main/dist">**Rilasci**</a> /
<a href="https://github.com/kudoai/chatgpt.js/discussions">Discutere</a> /
<a href="#">Torna in cima ↑</a>
