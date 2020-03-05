# Personal notes

Course: [https://www.coursera.org/learn/bootstrap-4/home/welcome](https://atom.io/packages/v-bootstrap4)
Instructor: Jogesh K. Muppala 
Associate Professor
Department of Computer Science and Engineering (Hong Kong University of Science and Technology)

*Notes created with MacDown*

## Source code?

Unfortunately [Courseras Honor Code](https://learner.coursera.help/hc/en-us/articles/209818863) permits the open sharing of source code from this course (I guess mainly because of the assignment tasks which would be openly available in the web). Therefore I keep the source code in a private repository by now.

## Tools 

### Atom & Atom Beautify: Indent Code 

Code-Editor: [https://atom.io/](https://atom.io/)

Choose [atom-beautify](https://atom.io/packages/atom-beautify) and click Install. Now you can use the default keybinding for atom-beautify CTRL + ALT + B to beautify your HTML ( CTRL + OPTION + B on a Mac)

`CTRL` + `ALT` + `B`

### Full page screen capture (Chrome)

Nice plugin mentioned by instructor, it does not need permission to access every website 
[](https://chrome.google.com/webstore/detail/full-page-screen-capture/fdpohaocaechififmbbbbbknoalclacl)

## Week 1: First project with lite-server

- Lite server ([https://www.npmjs.com/package/lite-server](https://www.npmjs.com/package/lite-server)) is quite nice because it will act as little local webserver (like MAMP or XAMPP), but it watches the project directory and refreshes the browser if a file was edited
- it is installed via `NPM = node package manager` from command line:

`npm init` <initializer> can be used to set up a new or existing npm package.
[https://docs.npmjs.com/cli/init](https://www.npmjs.com/package/lite-server)

1. `npm init` with index.html as entry point (instead index.js)
2. Use lite server for development purposes (local testing) and install it with this info via:
`npm install lite-server --save-dev`

3. edit package.json to use lite server to run the project locally:  
```
"scripts": {
  "lite":"lite-server",
  "start":"npm run lite",
  "test": "echo \"Error: no test specified\" && exit 1"
}
```

4. Launch the project: `npm start`

*(regarding 3.: In the coursera video "lite" is below start, which results in an error (script not found)
https://www.coursera.org/learn/bootstrap-4/lecture/L3Q8S/exercise-video-basics-of-node-js-and-npm at 14:00)*



## Week1: bootstrap4/conFusion

Work folder: /bootstrap4/conFusion/

1. npm install bootstrap@4.4.0 --save
2. npm install jquer@3.3.1 popper.ks@1.12.9 --save

(recommendation: use exact version instead of wildcard)

Committing to github, there was a vulnerability detected:
https://github.com/programmieraffe/coursera-frontend-end-2020/pull/1

Package.json was modified, updating jquery - there is a need to run "npm install" to apply those changes (afterwards jquery was updated)

Afer that:
> npm WARN bootstrap@4.0.0 requires a peer of popper.js@^1.12.9 but none was installed.

Tried:
npm install popper.js@^1.16.0 --save
(https://stackoverflow.com/questions/47039812/how-to-install-popper-js-with-bootstrap-4?rq=1)

## Bootstrap Grid System: Breakpoints

- col-sm-3 means, for sm + all sizes above sm = column with 3/12
- col-md-9, for medium (screen size ≥768px) + all screen sizes above medium = column width 9/12
> „Grid breakpoints are based on minimum width media queries, meaning they apply to that one breakpoint and all those above it (e.g., .col-sm-4 applies to small, medium, large, and extra large devices, but not the first xs breakpoint).“
https://getbootstrap.com/docs/4.0/layout/grid/

## Week1: Assignment - Hiding elements based on grid screen sizes

Hiding a div(p) only on xs (extra small) screens:

>	.d-none .d-sm-block

(d-none = hidden on all screens, d-sm-block: show this block on screen size smaller + all sizes above), See table here:
https://getbootstrap.com/docs/4.0/utilities/display/#hiding-elements

Also: Print styles
https://getbootstrap.com/docs/4.0/utilities/display/#display-in-print


## Week2

### Icon fonts:

> npm install font-awesome@4.7.0 --save
> npm install bootstrap-social@5.1.1 --save

### Forms

Grid system used in div.form-group row + label.col-md-2 + input.col-md-2 (medium screen size and above)

### Tables

dl = description list, format content inside, dt = description (list) termin (HTML5)
https://wiki.selfhtml.org/wiki/HTML/Textstrukturierung/dl
> <dl class="row">
>  <dt class="col-6">Started</dt>


### Media Object (images)
image positioned relative to content
https://getbootstrap.com/docs/4.0/layout/media-object/
- good for list of videos, articles,etc. with thumb previews

### Buttons
.btn-block for whole size of col
https://getbootstrap.com/docs/4.0/components/buttons/#sizes

## Week 3

Found out about [https://atom.io/packages/v-bootstrap4](https://atom.io/packages/v-bootstrap4) for Atom, found other nice plugins here:
[https://www.shopify.com/partners/blog/best-atom-packages](https://www.shopify.com/partners/blog/best-atom-packages)

### Modals

- Should be on top of the HTML page

### Carousel
- hiding the description / title on smaller devices is clever:

`<div class="carousel-caption d-none d-md-block">`

### Bootstrap uses jQuery for JS

## Week4 

### CSS Preprocessors

- popular: Less, Sass, Scss, Stylus
- bootstrap 4 is built with Sass, v3 used Less
- goal: overcome pain points of CSS
- nesting is supported

`#header .logo {
  width: 300px;
}`

becomes 

```
#header {
  color: black;
  .navigation {
    font-size: 12px;
  }
  .logo {
    width: 300px;
  }
}
```

- mixins: multiple props and values

```
.bordered {
  border-top: dotted 1px black;
  border-bottom: solid 2px black;
}
```

```
#menu a {
  color: #111;
  .bordered();
}
```

- mixins support parameters
- mathematical operations `height: $carousel-item-height*2`, color operations, etc.
- import operation possible (import sass/less files)

### Exercise: Less

- Less = Leaner Style Sheets [http://lesscss.org/](http://lesscss.org/)

Install and configuration of the node module for less:

1. `sudo npm install -g less@2.7.2` (g = global installation)
2. compiler "lessc" is now available an command line: `cd css` and use `lessc styles.less styles.css` (styles.css is generated from styles.less)

### Exercise: Scss

1. add as dev dependency for project `npm install --save-dev node-saas`
2. open up package.json, node-saas is listed in dev dependencies
3. add line to scripts `"scss": "node-sass -o css/ css/"` (-o = output directory, [input] and [output], both set to folder /css, see [https://www.npmjs.com/package/node-sass](https://www.npmjs.com/package/node-sass)) 
4. run `npm run scss`to convert less to css files

### Customize bootstraps SASS files

- bootstraps sass files can be imported, see: [https://getbootstrap.com/docs/4.3/getting-started/theming/](https://getbootstrap.com/docs/4.3/getting-started/theming/)


### Build scripts

- Install onchange/watch modules

`npm install --save-dev onchange@3.3.0 parallelshell@3.0.2`

### npmchange

> Use glob patterns to watch file sets and run a command when anything is added, changed or deleted.

[https://www.npmjs.com/package/onchange](https://www.npmjs.com/package/parallelshell)

Example:`onchange 'app/**/*.js' 'test/**/*.js' -- npm test`

### parallelshell

> This is a super simple npm module to run shell commands in parallel. All processes will share the same stdout/stderr, and if any command exits with a non-zero exit status, the rest are stopped and the exit code carries through.

[https://www.npmjs.com/package/parallelshell](https://www.npmjs.com/package/parallelshell)

### Configure watch (scss) + lite (package.json)

In scripts{}-section:
`"watch:scss": "onchange 'css/*.scss' -- npm run scss"`

Add this as parallelshell command, also in script{}

`"watch:all": "parallelshell 'npm run watch:scss' 'npm run lite'"`

Start scripts needs modification at last to use parallelshell instead of only "run lite"

`  "start": "npm run watch:all",`

Ran into an issues ([https://github.com/darkguy2008/parallelshell/issues/57](https://github.com/darkguy2008/parallelshell/issues/57)), downgrade to 3.0.1 (`npm install --save-dev parallelshell@3.0.1`), worked afterwards.

### Build distribution folder (only with node/usemin)

- dist/ folder (will be deployed to web server
- `npm install --save-dev rimraf@2.6.2` (module to delete folder completely) [https://www.npmjs.com/package/rimraf](https://www.npmjs.com/package/rimraf)
- `sudo npm install -g install copyfiles@2.0.0` ([https://www.npmjs.com/package/copyfiles](https://www.npmjs.com/package/copyfiles))

```
	"clean":"rimraf dist",
    "copyfonts":"copyfiles -f node_modules/font-awesome/fonts/* dist/fonts",
```

Test these changes:
1. `npm run copyfonts` (check out dist folder)
2. `npm run clean` (dist folder deleted)

- install imagemin ([https://www.npmjs.com/package/imagemin](https://www.npmjs.com/package/imagemin)) for img optimization

```
sudo npm install -g imagemin-cli@3.0.0 --unsafe-perm=true --allow-root
```

Use it in package.json:

`"imagemin":"imagemin img/* -o dist/img"`

**Important: Add dist folder to .gitignore**

#### usemin (+ cssmin + uglifyjs + htmlmin)

```
npm install --save-dev usemin-cli@0.5.1 cssmin@0.4.3 uglifyjs@2.4.11 htmlmin@0.0.7
```

> API version of usemin. For purists, those who doesn't use build tools like Grunt and Gulp, but just use node as their build tool.
[https://www.npmjs.com/package/usemin](https://www.npmjs.com/package/usemin)

usemin needs information in html source code (as html comment), which sections are relevant:

```
<!-- build:css css/main.css -->
<link rel="stylesheet" href="node_modules/bootstrap/dist/css/bootstrap.min.css" />
<link rel="stylesheet" href="node_modules/font-awesome/css/font-awesome.min.css" />
<link rel="stylesheet" href="node_modules/bootstrap-social/bootstrap-social.css" />
<link href="css/styles.css" rel="stylesheet" />
<!-- enbuild -->
```

Use it in package.json:

```
"usemin":"usemin contactus.html -d dist --htmlmin -o dist/contactus.html && usemin aboutus.html -d dist --htmlmin -o dist/aboutus.html && usemin index.html -d d dist --htmlmin -o dist/index.html"
```

Finally put all parts together:

1. clean dist folder
2. copyfonts
3. optimize images & output (-o) them to dist/img
4. run usemin for css/js minifcation

```
"build":"npm run clean && npm run copyfonts && npm run imagemin && npm run usemin"
```

#### View in browser

`npm run start` and navigate to [http://localhost:3000/dist/index.html](http://localhost:3000/dist/index.html)

#### package.json

Complete scripts{} in package.json
```
"scripts": {
    "start": "npm run watch:all",
    "test": "echo \"Error: no test specified\" && exit 1",
    "lite": "lite-server",
    "scss": "node-sass -o css/ css/",
    "watch:scss": "onchange 'css/*.scss' -- npm run scss",
    "watch:all": "parallelshell 'npm run watch:scss' 'npm run lite'",
    "clean": "rimraf dist",
    "copyfonts": "copyfiles -f node_modules/font-awesome/fonts/* dist/fonts",
    "imagemin": "imagemin img/* -o dist/img",
    "usemin": "usemin contactus.html -d dist --htmlmin -o dist/contactus.html && usemin aboutus.html -d dist --htmlmin -o dist/aboutus.html && usemin index.html -d dist --htmlmin -o dist/index.html",
    "build":"npm run clean && npm run copyfonts && npm run imagemin && npm run usemin"
  },
```

### Task Runners (Grunt and Gulp)

- Grunt: Configuration over Code (MIT license)
- Gulp: Code over Configuration (MIT license)

#### Grunt

1. install `npm install -g grunt-cli@1.2.0`
2. install locally `npm install grunt@1.0.2 --save-dev`
3. Create 'gruntfile.js'
4. `npm install --save-dev grunt-sass@2.1.0`
5. `npm install --save-dev time-grunt@1.4.0 jit-grunt@0.10.0`

jit-grunt
> A JIT(Just In Time) plugin loader for Grunt.
> Load time of Grunt does not slow down even if there are many plugins.

time-grunt (deprececated)

First add sass:

```
'use strict';

module.exports = function (grunt) {
    // Time how long tasks take. Can help when optimizing build times
    require('time-grunt')(grunt);

    // Automatically load required Grunt tasks
    require('jit-grunt')(grunt);

    // Define the configuration for all the tasks
    grunt.initConfig({
        sass: {
            dist: {
                files: {
                    'css/styles.css': 'css/styles.scss'
                }
            }
        }
    });

    grunt.registerTask('css', ['sass']);
};
```

test it in CLI: `grunt css`

6. `npm install --save-dev grunt-contrib-watch@1.0.0`
7. `npm install --save-dev grunt-browser-sync@2.2.0`

Add this to config as well in Gruntfile.js

```
// https://github.com/gruntjs/grunt-contrib-watch
        watch: {
          files: 'css/*.scss',
          tasks: ['sass']
        },
        // https://www.npmjs.com/package/grunt-browser-sync
        browserSync:{
          dev: {
            bsFiles:{
              src:[
                'css/*.css',
                '*.html',
                'js/*.js'
              ]
            },
            options:{
              watchTask: true,
              server:{
                baseDir: './'
              }
            }
          }
        }
```

Add task: 
```
grunt.registerTask('default'['browserSync','watch']);
```

Just run `grunt` afterwards to use default task

## Other notes

### GitHub desktop

It is not a full featured Git-Client, going back to a previous commit is not possible currently ([https://stackoverflow.com/questions/34790794/going-back-to-a-previous-commit-in-github-desktop](https://stackoverflow.com/questions/34790794/going-back-to-a-previous-commit-in-github-desktop))

Tried GitKraken, but it does not support private repos in free version.