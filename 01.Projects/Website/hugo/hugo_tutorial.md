# How to Create a Static Website with Hugo: Windows


followed this tutorial series: https://www.youtube.com/watch?v=qtIqKaDlqXo&list=PLLAZ4kZ9dFpOnyRlyS-liKL5ReHDcj4G3

## Setting Up Hugo
1. we have to create some folders. `C:\Hugo\bin`
2. The we have to download the binaries from the github page: https://github.com/gohugoio/hugo/releases. 

```ad-note
color: 200, 200, 200

I got the windows 64 bit hugo extended binary becuse I would like to play around with sass/scss in the future
```
3. Once you have the binaries downloaded then you will have to extract them the the `C:\Hugo\bin` location.
4. Next you will have to add the`C:\Hugo\bin` lcoation to your [[windows_path]]

## Folder Structure of Hugo

- **archetypes:** A piece of content that is common throughout the site.
- **contest:** This is where all the web pages/content will go.
- **data:** This is were the data such as json files or csv files will go
- **layouts:** Where your layouts common throughout the site will go. For example if you want a header and sub-header
- **static:** Data that is not changed throughout the site. Such as images and csv files
- **themes:** Where the themes for your website goes.
- **config.toml:** Basically the settings for the entire website.

## First Website

basically you type the command:

```shell
hugo new site <name of the site>
```

This will create a folder in the directory that your ran the command  with the same name that you passed as the name of your site.


## Installing and Using Themes

You can find a bunch of themes for hugo at: https://themes.gohugo.io/

Each theme will be a github repo. You can then [[git clone]] the repo into the themes folder of your hugo webite.

You then have to open up the config.toml file and add the line `theme = "<name of the theme you downloaded>"`

```toml
baseURL = 'http://example.org/'
languageCode = 'en-us'
title = 'My New Hugo Site'
theme = "<name of the theme you downloaded>"
```

to test that everything is working run the command:

```shell
hugo server
```

and the website should be able to be viewied as a local host.

## Creating and Organising Content

This will be theme dependent

Using this command:
```shell
hugo new a.md
```
we can create a file in the **content**  ([[folder_structure]]) folder called a.md that conatains some meta data. The meta data is the data contained in the **archetypes**([[folder_structure]]) folder under the file `default.md`

we then have to build the statuc files. This is achieved with the command:
```shell
hugo server --buildDrafts
```
This means that the content files that have the line `draft: true` in them will be built.

We can also create directory structures too:
```shell
hugo new dir1/b.md
```
When this happens the file structure will be displayed instead of just a list of the files.

You can have two types of content:
1. List pages: that contains a list of all the content files
2. Single pages: contains the actual content that you want (whats inside the md file)

```ad-note
color: 200,200,200

Only directories one level deep in the content file [[folder_structure_of_hugo]] will be displayed in the list content page as directories. All other directories wont be shown and instead all of their files will be listed in the top level directory.

"*Hugo will only automatically create list pages for folders in the root level of the content folder.*"

```


However, this can be solved. by creating a list page manually.

If we add a `_index.md` file to a directory that we want to become a list page.
```shell
hugo new dir1/dir2/_index.md
```
You can also modify the `_index.md` file to add content directly to the page. For example you could write in it as if it was a regular md file or you could change the title by changing he `title: "<name of your title>"` line at the top of the `_index.md` file.


## Front Matter

This is meta data for our content file. Hugo automatically add in data to content files when they are created and this is called front matter. The data is normally in key value pairs.

example: yaml
```yaml
---
title: "Dir2"
date: 2021-09-25T18:11:39+01:00
draft: true
---
```

example: toml
```toml
+++
title = "Dir2"
date = 2021-09-25T18:11:39+01:00
draft = true
+++
```

The data in the front matter can be seen in the cards for the content files. This is theme dependant

## Archetypes

These are responsible for the automatic front matter that is created when you create a new content file page.

We can modify the `default.md` file that will be the default archetype for all conetnt files. However, we can also define archetypes for specific directories.

To do this we hace to define a markdown file in the archetype [[folder_structure]] folder with the same name of the directory that we have in the content folder [[folder_structure]].

Example: defauly.md
```yaml
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
---
```

Example: dir1.md
```yaml
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
author: "Stever"
---
```

## Shortcodes

They are predefined html code that can be put into markdown files.

example of using a pre-written shortcode to add a youtube video by editing a markdown file.

```markdown
{{< youtube 2xkNJL4gJ9E >}}
```

## Taxonomies

Ways to group pieces of content together.

All taxomies are declared in the [[front_matter]].

Example:
```yaml
---
title: "A"
date: 2021-09-25T17:40:02+01:00
draft: true
author: "Ruairidh"
tags: ["tag1", "tag2", "tag3"]
categories: ["cat1"]
---
```

now depending on the theme that you are using you can group together all the single pages of content together into a list page by the tag or catagory that they are assocaited with.

you can also define you own taxomies by adding them directly to the [[front_matter]]. 

```ad-note
color: 200,200,200
This is specific to the theme package that you use
```

Example:
```yaml
---
title: "A"
date: 2021-09-25T17:40:02+01:00
draft: true
author: "Ruairidh"
tags: ["tag1", "tag2", "tag3"]
categories: ["cat1"]
moodes: ["Happy", "Upbeat"]
---
```

now we have to tell hugo about our new taxomie. To do this, you have to go to the `config.toml` file in your website directory and add in a section:

```toml
baseURL = 'http://example.org/'
languageCode = 'en-us'
title = 'My New Hugo Site'
theme = "ga-hugo-theme"

[taxonomies]
tags = "tags"
category  = "categories"
moood = "moods"
```

## Template Basics

To create a theme in hugo you use templates.

A template is piece of html that are common for all types of pages. The pages can be list pages or single pages.

### Sinlge Page Templates

Noramlly this will be defined for you in the theme folder [[folder_structure]] however if you would like to modify this then you will have to go to the file `theme/<name of the theme>/layouts/_default/single.html` This will allow you to edit the html for the theme.

If you want to overwrite the theme or create your own then you have to go to the layour folder [[folder_structure]] in your website root direcotry and add in the directory `_default` and then define a html called singe `single.html`

Lets have a look at an example of a custom html file.

```html
<html>
	<head>
	 <meta charset="UTF-8">
	 <title>Document</title>
	</head>

	<body>
	 <h1>Header</h1>
	 <hr>
	 <h3>{{.Title}}</h3>
	 <h4>{{.Date}}</h4>
	 {{.Content}}
	 <hr>
	 <h2>Footer</h2>
	</body>
</html
```
To access the [[front_matter]] data you will have to use the symtax `{{.<name of the variable>}}` noting that the name of the variable will be capatalised. Also note that the variable `{{.Content}}` is all of the mardown content contained in the single page mardown file.

### Home Page Template

defing your custom html for the home page by adding the file `index.html`to your layouts [[folder_structure]] folder

### Section Templates

When we want to define a cutsom template/html for a certain directory in the content folder [[folder_structure]]. We can do this with section templates.

In the layouts folder [[folder_structure]] we will define a directory that has the same name as the directory within the content folder. Within this file we can define custom single and list page html templates

### Base Templates and Blocks

To make your site more modular it would be a good idea to have a base html file that both the list and the single pages could read from.

To do this we define a file in `layouts/_default/baseof.html` this is parent file for the single and list html files used.

Example: baseof.html

```html
<html>
	
<head>
 <meta charset="UTF-8">
 <title>Document</title>
</head>

<body>
 Top of baseof
 <hr>
 {{ block "main" . }}
  
 {{end}}
 {{ block "footer" . }}
 This is th default baseof Footer
 {{end}}
 <hr>
 Bottom of baseof
</body>

</html>
```

Example: list.html

```html
{{ define "main" }}

 This is the list template

{{end}}
```

Example: single.html
```html
{{ define "main" }}
 This is the single template
{{end}}

{{ define "footer" }}
 This is the single footer
{{end}}
```

As you can see we can effectively overide certain sections if we would like.

## Variables

You can't access variables in markdown files.

So how do you access variables. You will define the variables in the specific [[front_matter]] that is defined as yaml or toml or json . These are the variables that you can access and customise at will.

inside either the list.html or the single.html templates you should use the syntax

```html
{{ .Title }}
{{ .URL }}
{{ .Params.myVar }}
```

this wil work with a single page that has front matter that matches this:

```yaml
---
title: "B"
date: 2021-09-25T17:46:46+01:00
draft: true
myVar: "myValue"
---

```

now lets create a completely custom variable that is completely compatible with html

```html
{{ $myVarName := "aString" }}
{{ $myVarName }}

<h1> {{ $myVarName }} </h1>
```

We can checkout all the different variables we can access here: https://gohugo.io/variables/

## Function in Variable

If you want to use function inside the code that acts on the variables defined in the [[front_matter]] or that come pre-defined with hugo the it works like this

```html
{{ myFunc param1 param2 }}
```

Examples being:
```html
{{ truncate 10 "This is a really long string"}}

{{ add 1 5 }}

{{ singularize "dogs" }}

{{ range .Pages }}

{{ .Title }} <br>

{{end}}
```

The buit in functions can all be found here: https://gohugo.io/functions/

## Conditionals

I think it would be better to just see some examples of the synax of how the work

```html
 {{ $var1 := "dog" }}
 {{ $var2 := "cat" }}

 {{ $var3 := 3 }}
 {{ $var4 := 4 }}

 {{ if not (eq $var1 $var2) }}
 <h1>The if statement was true</h1>
 {{else}}
 <h1> Ths if statement was false</h1>
 {{end}}

 <br>

 {{ if and (lt $var3 $var4) (lt $var4 $var3)}}
 <h1>The if and statement was True</h1>
 {{else}}
 <h1>The if and statement was False</h1>
 {{end}}
```

## Data Files

Form [[folder_structure]] the data folder can be thought of as a mini database that just contains data. It should be similar to the [[front_matter]] data structure. Therefore we are dealing with yaml, json or toml files.
 
so how do we access this data.

Data file:
```json
{

 "WA": {

 "name": "Washington",

 "capital": "Olympia"

 }

}
```

The single.html
```html
 {{ range .Site.Data.states }}

 {{ .name }}

 {{end}}
```

## Partial Templates

In the layour folder [[folder_structure]] we should create folder called partials and inside the folder you should create html files.

Example partial: header.html
```html
<h1> {{ .Title }}</h1>
<p>{{ .Date }}</p>

<hr>
<br>
```

How do you access this partial:
```html
{{ partial "heaer" . }}
```

this can be added to any part of the layout html files.

But what is the dot. The do is just the scope of what variables are passed to the partial. So in the case of puting the dot then the entire scope is added to the partial and the partial can use any variable.

But, lets say that we would like to pass a dict to the partial

```html
{{ partial "heaer" (dict "myCustomTitle" "myTitle" "myCustomDate" "myDate") }}
```

now when this is called the partial will only have access  to `myCustomTitle` or `myCustomDate`

## Shortcode Templates

These are the same as partial templates but we can use them in the markdown files.

Just like in partials we will have to create a folder in the layout directory [[folder_structure]]
and call it `shortcodes`. In side the shortcodes folder we can then define out shortcode html.

Example: shortcode html
```html
<p style="color:{{ .Get `color`}}">This is the shortcode text</p>
```

we can make an observation here that the shortcode recieves an argument.

Example: shortcode.md
```md
{{< myshortcode color="blue">}}
```

```ad-note
color: 200,200,200

The arguments to the shorcode can be passed in by name or postion
```

Now what if we have a lot of text that we want to use inside a shortcode we can use the `{{ .Inner }}` variable.

Example: shortcode.md
```md
{{< myshortcode >}}
	This is the text inside the shortcode
{{< /myshortcode >}}
```

Example: shortcode.html
```html
<p style="background-color:yellow;"> {{ .Inner }}</p>
```

## Building to Host the Site

To build all the files so that we can deploy the website we can run a hugo command.

```shell
hugo
```
This will build the website and put the files into a folder called `public` that can be found in the website folder.

```ad-note
color: 200,200,200
You will have to delete the public folder first before re-building the hugo website
```