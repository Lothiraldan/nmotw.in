---
layout: post
title: "block.js"
date: 2014-04-24 19:12:16 +0530
comments: true
categories: templating 
ogimg: http://nmotw.in/images/block.js/block.js.gif
---

[Block.js](https://www.npmjs.org/package/block): Ridiculously simple HTML templating. All it does is replaces "blocks" in your template with a local.

The crux of this module is in these simple lines of code:

```javascript
function replace(string, key, value) {
  return string.replace(
    new RegExp('\\{\\{\\s*' + escapeRegExp(key) + '\\s*\\}\\}', 'g'),
    value || ''
  )
}

function escapeRegExp(str) {
  return str.replace(/([.*+?=^!:${}()|[\]\/\\])/g, '\\$1')
}
```

The API is also pretty simple:

```javascript
var template = Block(html);
//html is a string, and block returns a new templating instance.

template.render(locals); 
//locals is an object of "blocks" to replace in the template.
```

__Simple Example:__

```javascript
var block = require('block')
, fs = require('fs')
, tmpl = fs.readFileSync('block.html', 'utf-8')
, data = block(tmpl).render( {content: '<div class="inner"></div>'});

console.log(data);
```

__GIF GTW!:__
![block](/images/block.js/block.js.gif)


Hope you liked this simple HTML templating engine! Go ahead and `.replace('{{block}}', string)` 

Thanks to the author [Jonathan Ong](http://jongleberry.com).


