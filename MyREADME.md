### Some notification for later modification of the Blog:

1. Know hierarchy of files: <br>
   `_config.yml` ------------> configure sidebar panel and reference links <br> 
   `Hamid Manouchehri` tab ------------> `README.md` <br>
   `Projects` tab ------------> `projects.html` ------------> `_posts/` 
2. Considering loading commits takes time, wait for some minutes to see output of your modification in your Blog. Frequent commits may lead you to make the mistake of that some changes does not work, or you have something wrong with the code, whereas, there is nothing wrong, but previous change have not been deployed yet.
3. Right caption: `Fig. 1`  &emsp;&emsp;&emsp;&emsp;&emsp; Wrong caption: `Fig.1`
4. Crop images with minimum border to have become more suitable in terms of vertical margins in webpages.
5. Do not add comment to `projects.html` and `archive.html`, otherwise it makes problem to load including sources.
6. Do not change `_posts/` files into `html`, it is easier to work with [markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) syntax and even it supports `html`.
7. Sometimes page `refresh` does not function, to see the changes of commits, so it is a good idea to close the tab and open it again: <br>
   `setting` > `pages` > link of the blog
8. To generate equations for the web pages, go to [CODECOGE](https://www.codecogs.com/eqnedit.php), write your equation and remember to select `HTML` output. To label you equation, at the end of equation put `;` then write `equ(number_of_equation)`.
9. When you rush to do something, just find the __easiest way__ nor the efficient or perfect one. As an example, it is a bit hard to insert multiple images in a row with separate captions via `HTML`, because you'll need to create `responsive` web pages to avoid inappropirate loading of the contents of your webpages in different browsers, of course it is cumbersome to do them all without web development _frameworks_. Just take it easy and firstly edit images in `LibreOffice Word`, align them in a row and insert caption, then take export it as an image file or more easier, take an screenshot, then upload it as a single image in `HTML`.
10. The `Preview` tab does not work properly for some modifications occasionally, so it's better to check the results in the webpages.
11. __Important Note__: When there something wrong with the code, rendering, style or anything else, remember that there is nothing wrong with the servic, parser, or etc. It is, in _99.9%_ of occurrences, a human mistake, just check your code again, _double check_, triple check, and if you can not find it, get help from others, ask someone to take a look at your code. __It is sometimes hard to see the most obvious faults as point of your view__.
12. To enter _Greek letters_ within a sentence, you have two options:
      1. Insert in _Markdown_ syntax: `$$\greek_letter_name$$`, it is true for other mathematic expressions, e.g. `$$A^T_{\alpha}$$`
      2. Insert in _HTML_ syntax: `&greek_letter_name;`
