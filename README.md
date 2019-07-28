[Bible.js] - Load bible partially in JSON format
=============================================

What is Bible.js
-------------
Bible.js is a javascript library to partially load JSON bible chapter to the client browser for further processing, without the need to rely on server-side processing.
The data is between 1-10Kb, allowing fast loading for further usage and ideal to be cached for CDN.
The JSON passage data can be accessed directly as github allows CORS.

Initially the library was prepared was using LZW compressed JSON to reduce the size.
However, the decompression process may become very slow for old phones.
Plain JSON allowing fast loading and text cached by the browser, further processing such as regenating the entire database on client storage.

See [Lzbible](https://github.com/edwinyosorahardjo/lzbible) and fork it or contribute to the repository.

Bible.js is suitable for
-----------------------
 * javscript bible app
 * mobile application

Bible data is converted from the following source:
--------------------------------------------------
[bibledatabase.org](http://bibledatabase.org/bibles.html)

Examples
--------

### Direct access JSON files
```
// available bibles
http://[url]/db/bibles.json

// book index
http://[url]/db/[bible]/books.json
e.g. http://bible.js.org/db/kjv/books.json

// bible chapters
http://[url]/db/[bible]/[book]_[chapter].json
e.g. http://[url]/db/kjv/1_1.json
```

### Inclused LzBible.js and required scripts
```    
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
<script type="text/javascript" src="../js/jsonbible.js"></script>
```

### Init LzBible - when url is not added it uses local /db/
```
var bibles = await JsonBible.Init('http://bible.js.org/db/');
JsonBible.SetBible(bibles[0]);
```

### Get books
```
var books = await JsonBible.GetBooks();
```

### Get array of chapters for given book idx 0..65
```
var chapters = JsonBible.GetChapters(0..65);
```

### Get passages/verse array with non-zero idx (starts from 1)
```
var verses = await JsonBible.GetPassages(bookIdx, chapterIdx);
var verses = await JsonBible.GetPassages(1, 1); // genesis, ch 1
```

### Sample Bible App using Vue JS
[View Here](sample/index.html)


TODO
----
 * convert more bibles
 * more test cases


