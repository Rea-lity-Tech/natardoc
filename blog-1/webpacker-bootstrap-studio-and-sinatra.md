---
description: >-
  In this guide we describe how we created a pipeline to design a webpage in
  Bootstrap Studio, call a Sintra API and make everything nice and reactive with
  StimulusJS distributed by Webpacker.
---

# Webpacker, Bootstrap Studio, and Sinatra

## Is this a winning mix ?

We wanted to have similar languages and uses between our Sinatra and Rails applications. Here is our creation process:

1. `HTML/CSS` Design the page with Boostrap Studio, with or without a template.  
2. `Bash`  Export Boostrap Studio creations to a Sinatra project.  
3. `Ruby` Create a backend API in Sinatra to populate the pages. 
4. `JS/ES6` Make everything nice and reactive with modern Javascript.
5. Have all steps refresh as instantly as possible for live coding. 

{% hint style="success" %}
Once the application is built for production, only Sinatra is required.
{% endhint %}

The interactive creation process is quite easy and pleasant to use. During the design phase  Bootstrap studio automatically reloads the browser when anything changes, even when webpacker updates its bundled output ! Sinatra has gem for [hot reload](http://sinatrarb.com/contrib/reloader) and webpacker's dev server is very reactive. 

The only current limitation is the export process between BS Studio and Sinatra that connot be triggered automatically. There also many small differences between dev and production. 

> In development mode there are three running web servers, each on its own port: Boostrap Studio preview \(8000\), Sinatra \(4567\), and Webpack dev server \(8080\).

### Webpacker

We use webpacker to compile our [Stimulus](https://stimulusjs.org/) code. 

{% hint style="info" %}
You can check out the [gist](https://gist.github.com/poqudrof/08fcdeaddd1eec56f664dad679d9f1da) of our project to configure webpacker.  [  ](https://gist.github.com/poqudrof/08fcdeaddd1eec56f664dad679d9f1da)
{% endhint %}

#### Installation

You need to have npm and yarn installed to install webpacker. You can the get the packages required. 

```
$ yarn install
```

Then you can either run in development or production. 

```text
$ yarn start  ## to start the development server
$ yarn build  ## to create the dist/natar.bundle.js
```

Be sure to have the correct file organization: 

* `/node_modules`
* `/dist`
* `/src/index.js`
* `/src/controllers/hello_controller.js`
* `package.json`
* `webpack.config.js`

In our project, we edited it to add webpacker in the same folder as our sinatra server: 

* `/node_modules`
* `/packs/src/index.js`       _`(Webpack entry point)`_
* `/packs/src/controllers/hello_controller.js`  _`(Stimulus controllers)`_
* `/public/assets/packs`   _`(folder for the generated files)`_
* `/views/...`     _`(Sinatra views)`_
* `package.json`
* `webpack.config.js`

You can start Sinatra and webpacker in one command with foreman: 

`$ foreman start`

You just need a `Procfile` file in the sinatra folder: 

{% code title="Procfile" %}
```text
web: bundle exec ruby nectar.rb
pack: yarn start 
```
{% endcode %}

#### Switch to production 

To switch from development to production and the opposite in Bootstrap Studio or directly in Sinatra: 

1. Remove the external  Javascript link: `http://localhost:8080/natar.bundle.js`.
2. Build the bundle:  `$yarn build`  and get the output file: `dist/natar.bundle.js`. 
3. Add a local Javascript link: `js/natar.bundle.js`  to layout.hmtl. 
4. Add the file to your public folder, if you added the file to Bootstrap Studio it is already done. 

## Bootstrap Studio 

We use Bootstrap Studio to manage the assets and most of the HTML/CSS code in the application. It does not alter the generated HTML code between the development phase and exports. BS Studio handles links between dom elements to share code between pages, or partials if we use Rails vocabulary. 

In BS Studio we create a `layout` page, that is used nearly as is in Sinatra. It contains some ERB code to change some elements such as the current page name. All the other pages contain links to this layout, but only the content is used. 

{% hint style="info" %}
The content of a page created in BS Studio is extracted with the`pup` command. We extract the HTML from the first  `.content`element. 
{% endhint %}

#### Conversion from BS Studio to Sinatra 

The pages exported in BS Studio store the assets \(HTML/CSS/JS\) in an `asset` folder. So we created a script to move the exported files, change de file names from HTML to ERB.

{% hint style="danger" %}
Do not export your Bootstrap Studio project directly to the Sinatra project. This deployment script deletes the existing assets. 
{% endhint %}

{% code title="export\_bs\_to\_sinatra.sh" %}
```bash
#!/bin/bash

cd $1

## remove previous release
rm -rf public

mkdir public

# move the asset folder. 
mv assets public/

## Extract the layout 
mv layout.html layout.erb

## Remove the layout
## pup-bin in AUR
pup ".content" < index.html > index.erb
pup ".content" < device.html > device.erb
## ...

## remove previous release
rm -rf views

## Move the pages to view folder
mkdir views
mv *.erb views/

## remove temporary pages. Disable warning.
rm *.html 2> /dev/null 
rm *.html.tmp 2> /dev/null 

```
{% endcode %}

 

## Run the project with Sinatra



`bundle exec ruby nectar.rb`

