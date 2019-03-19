---
title: Adobe Campaign helpers
categories: [opensource,adobe campaign,tools]
---
Excerpt here...
<p class="text-center">🐍👑🌍</p>
<!--more-->

## SQL helpers

```js
/**
 * Performs an SQL INSERT INTO (no SQL injection protection /!\)
 * @param {object} fields {column1:value1, column2:value2}
 * @returns {number} The number of inserted fields
 * @see sqlExec
 */
function insertInto(table, fields, log){
  if(undefined === log){
    log = false;
  }
  var columns = Object.keys(fields).join(', ');
  var values = Object.keys(fields).map(function(key) {
    var value = fields[key];
    // if it's a string
    // - remove all ' with regex /'/g
    // - wrap with single-quote
    if(typeof(value) == 'string'){
      value = value.replace(/'/g, "");
      value = "'"+value+"'";
    }
    // if it's null, use 'null'
    else if(value == null){
      value = 'null';
    }
    return value;
  }).join(', ');
  var sql = "INSERT INTO "+ table + " ("+columns+") VALUES ( "+values+" )";
  if(log){
    logInfo('Executing '+sql)
  }
  return sqlExec(sql);
}
```

## Linux server helpers
```js
/**
 * Helper for the ACC execCommand() function
 * @param {string} command the linux command to execute
 * @param {Object} params parameters [to be flexible for evolutions]
 * @param {bool} params.logTheCall if true, calls logInfo(command)
 * @param {bool} params.logTheOutput if true, send the output to logInfo
 */
function exec(command, params){
  if(params.logTheCall){
    logInfo('fresh:helpers | executing | '+command);
  }
  var list = execCommand(command)[1];
  var lines = list.split("\n");
  if(params.logTheOutput){
    for each (var line in lines){ 
      logInfo("" + line);
    }
  }
  return lines;
}

/**
 * Calls unix sed to replace a text by another text, in a file
 * Usage of sed: 
 * - sed -i s/regular-expression/replacement-text/flags
 * - -i replace in file instead of in string
 *
 * @param {string} replaceThis the regex to look for
 * @param {string} byThis the string write instead
 * @param {string} inThisFile full path of the file
 * @param {Object} params for exec() params
 *
 * @see https://doc.ubuntu-fr.org/sed
 *
 * TODO replace | by [|] because pipe | in the sed regex must be escaped with [|]
 */
function replaceInFile(replaceThis, byThis, inThisFile, params){
  var command = "sed -i 's/"+replaceThis+"/"+byThis+"/g' '"+inThisFile+"'";
  return exec(command, params);
}
/**
 * Remove carriage returns '\r' in file
 * @param {string} fileFullpath the full path of the file
 * @param {Object} params for exec() params
 */
function removeCarriageReturn(fileFullpath, params){
  replaceInFile('\r', '', fileFullpath, params)
}
```