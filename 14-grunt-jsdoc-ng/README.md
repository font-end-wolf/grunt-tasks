## [Blog post](http://grunt-tasks.com/grunt-jsdoc/ "grunt jsdoc")

Grunt jsdoc-ng is an awesome grunt plugin that allows you to create documentation automatically from your javascript source code in your build process itself.
Bonus point is that the docs which are generated is a single page web app based on angular-js for faster navigation.

> We wont be using grunt-jsdoc because of [this issue](https://github.com/krampstudio/grunt-jsdoc/issues/124)

jsdoc is a javascript documentation generation framework used to build custom documentation based on your source code comments. Using its block tags you can have a beautiful documentation of your code/API.
By making use of grunt jsdoc you are removing the work of maintaining your code documentation. It is extremely important to keep your source code documented and an easy to use API.

> For more information on how to use jsdoc please visit [jsdoc](http://usejsdoc.org/ "jsdoc")

![sublime-jsdoc](https://camo.githubusercontent.com/415148aecc6dac2e5ebb12b7f7584f4a8744eca4/687474703a2f2f73706164676f732e6769746875622e696f2f7375626c696d652d6a73646f63732f696d616765732f66756e6374696f6e2d74656d706c6174652e676966 "sublime-jsdoc")

> If you are using sublime then there's an awesome [plugin](https://github.com/spadgos/sublime-jsdocs) to create comments for your code:

## Getting it all set up

To install grunt-jsdoc-ng:

`npm install --save-dev grunt-jsdoc-ng`

Lets consider a simple javascript file `area.js` which encompasses the @Area constructor and its methods and properties.
It has got getters like fetching its width, its height, its total area and setters for setting its width or height.

Here's the corresponding section in Gruntfile.js
```
 grunt.initConfig({
    'jsdoc-ng' : {
      dist : {
        src: ['src/*.js', 'README.md' ],
        dest: 'docs',
        template : 'jsdoc-ng',
        options: {
        }
      }
    }
  });
```

Here's the source code for area.js:
and here's the [link](https://rawgit.com/kanakiyajay/grunt-tasks/master/14-grunt-jsdoc-ng/docs/index.html#!/Area) to what the generated documentation looks like.

```js
"use strict";
/**
 * Creates a new geometrical Area Block
 * @param {int} width  the width of the area
 * @param {int} height the height of the area
 */
function Area(width, height) {
  this.width = width;
  this.height = height;

  /**
   * Returns the width of the area
   * @return {int}      the width of the area
   */
  this.getWidth = function() {
    return this.width;
  };

  /**
   * Returns the height of the area
   * @return {int}      the height of the area
   */
  this.getHeight = function() {
    return this.height;
  };

  /**
   * Returns the 2D area of the object
   * @return {int} height x width
   */
  this.getTotalArea = function() {
    return this.height * this.width;
  };

  /**
   * Returns whether height or width is greater
   * @return {string}
   */
  this.getGreater = function() {
    var greater = this.height > this.width ? "height" : "width";
    return greater;
  };

  /**
   * Changes the Height of the area
   * @param {int} ht new height
   */
  this.setHeight = function(ht) {
    this.height = ht;
    return ht;
  };

  /**
   * Changes the Width of the area
   * @param {int} wd new width
   */
  this.setWidth = function(wd) {
    this.width = wd;
    return wd;
  };
}
```

On running grunt from the command line

```
$ grunt
Invoking JsDoc
Parsing H:\grunt-tasks.com\github\14-grunt-jsdoc-ng\src\area.js ...>> complete.
Generating output files...
>> Output minification enabled
>> Minifying JavaScript output
Writing output files...>> complete.
>> Finished running in 1.21 seconds.

JsDoc completed
```
It will automatically create the documentation from our comments in area.js, format it and output a beautiful html file containing the docs. It will parse our READMEmd file and generate its documentation.

> In this app, because I am fetching the README.md and posting it on this blog post, the jsdoc documentation generated will also contain the blog post.

This the final tree structure of our app:

```
.
├── docs
│   ├── fonts
│   │   ├── fonts.min.css
│   │   ├── LICENSE.txt
│   │   ├── Ubuntu-Bold.ttf
│   │   ├── Ubuntu-BoldItalic.ttf
│   │   ├── Ubuntu-Italic.ttf
│   │   ├── Ubuntu-Light.ttf
│   │   ├── Ubuntu-LightItalic.ttf
│   │   ├── Ubuntu-Medium.ttf
│   │   ├── Ubuntu-MediumItalic.ttf
│   │   ├── UbuntuMono-Bold.ttf
│   │   ├── UbuntuMono-BoldItalic.ttf
│   │   ├── UbuntuMono-Italic.ttf
│   │   ├── UbuntuMono-Regular.ttf
│   │   └── Ubuntu-Regular.ttf
│   ├── index.html
│   ├── jsdoc-ng.data.js
│   ├── jsdoc-ng.min.css
│   ├── jsdoc-ng.min.js
│   └── libs
│       ├── angular.min.js
│       ├── angular.min.js.map
│       ├── highlight.min.css
│       └── highlight.min.js
├── Gruntfile.js
├── package.json
├── README.md
└── src
    └── area.js
```

Here'a [link](https://rawgit.com/kanakiyajay/grunt-tasks/master/14-grunt-jsdoc-ng/docs/index.html#!/Area) to the documentation generated and the screenshot is below

![grunt-jsdoc-ng](http://i.imgur.com/FoXba8Z.jpg)

You can find all the other options for grunt-jsdoc-ng below.