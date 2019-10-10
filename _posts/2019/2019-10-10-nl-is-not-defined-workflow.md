---
title: "NL is not defined" error while compiling workflow
categories: [opensource,adobe campaign]
---

Excerpt here...
<p class="text-center">🐍👑🌍</p>
<!--more-->

## "NL is not defined" exception
```console
10/10/2019 9:56:45 AM	js3	JST-310000 Error while compiling script 'WKF1096688/js3' line 2: NL is not defined.
```

```js
NL.require('/nl/core/sql.js'); // @throws Exception

var enumName = 'city';
var enumId = sqlGetDouble ('SELECT iEnumId FROM xtkEnum WHERE sName='+NL.SQL.escape(enumName));
```

Add `loadLibrary("/nl/core/shared/nl.js");` first:

```js
loadLibrary("/nl/core/shared/nl.js");
NL.require('/nl/core/sql.js'); // OK

var enumName = 'city';
var enumId = sqlGetDouble ('SELECT iEnumId FROM xtkEnum WHERE sName='+NL.SQL.escape(enumName));
```

PS: doc for `NL.SQL.escape` https://final-docs.campaign.adobe.com/doc/AC/en/jsapi/p-8.html

See [NL.Locale to format prices tuto](/2019/05/adobe-campaign-locale)
