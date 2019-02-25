![](/mdfile/images/logo.png)  
![](https://img.shields.io/badge/version-1.0-blue.svg)
### Introduction
----
sillyhat-hugo is a learning hugo project.  

#### Install
----
1. Install hugo

`brew install hugo`

`hugo version`

2. Create a New Site

`hugo new site sillyhat-hugo`

3. Add a Theme

`cd sillyhat-hugo`

`git init`

`git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke`

`echo 'theme = "ananke"' >> config.toml`

3. Add Some Content

`hugo new A.md`

![](/mdfile/images/hugo-new-site.png)

4. Start the Hugo server

`hugo server -D`

**Navigate to your new site at http://localhost:1313/**
![](/mdfile/images/start-server.png)

#### Used
----

_传递参数到**partials**目录下的**header.html**文件_
* 定义kind字段，value值为：[{{ .Kind }}](#.kind)
* 定义Template字段，value值为：List
```
{{ partial "header" (dict "Kind" .Kind "Template" "List") }}
```

#### Variables
----
Hugo’s templates are context aware and make a large number of values available to you as you’re creating views for your website.

##### Site Variables
使用方式
```
{{ $.Site.Params.author }}
{{ $.Site.Params.description }}
```
![](/mdfile/images/site-variables-config.png)
----
**.Site.AllPages**
```
array of all pages, regardless of their translation.
```
**.Site.Author**
```
a map of the authors as defined in the site configuration.
```
**.Site.BaseURL**
```
the base URL for the site as defined in the site configuration.
```
**.Site.BuildDrafts**
```
a boolean (default: false) to indicate whether to build drafts as defined in the site configuration.
**.Site.Copyright**
```
a string representing the copyright of your website as defined in the site configuration.
**.Site.Data**
```
custom data, see Data Templates.
```
**.Site.DisqusShortname**
```
a string representing the shortname of the Disqus shortcode as defined in the site configuration.
```
**.Site.Files**
```
all source files for the Hugo website.
```
**.Site.GoogleAnalytics**
```
a string representing your tracking code for Google Analytics as defined in the site configuration.
```
**.Site.Home**
```
reference to the homepage’s page object
```
**.Site.IsMultiLingual**
```
whether there are more than one language in this site. See Multilingual for more information.
```
**.Site.IsServer**
```
a boolean to indicate if the site is being served with Hugo’s built-in server. See hugo server for more information.
```
**.Site.Language.Lang**
```
the language code of the current locale (e.g., en).
```
**.Site.Language.LanguageName**
```
the full language name (e.g. English).
```
**.Site.Language.Weight**
```
the weight that defines the order in the .Site.Languages list.
```
**.Site.Language**
```
indicates the language currently being used to render the website. This object’s attributes are set in site configurations’ language definition.
```
**.Site.LanguageCode**
```
a string representing the language as defined in the site configuration. This is mostly used to populate the RSS feeds with the right language code.
```
**.Site.LanguagePrefix**
```
this can be used to prefix URLs to point to the correct language. It will even work when only one defined language. See also the functions absLangURL and relLangURL.
```
**.Site.Languages**
```
an ordered list (ordered by defined weight) of languages.
```
**.Site.LastChange**
```
a string representing the date/time of the most recent change to your site. This string is based on the date variable in the front matter of your content pages.
```
**.Site.Menus**
```
all of the menus in the site.
```
**.Site.Pages**
```
array of all content ordered by Date with the newest first. This array contains only the pages in the current language. See .Site.Pages.
```
**.Site.RegularPages**
```
a shortcut to the regular page collection. .Site.RegularPages is equivalent to where .Site.Pages "Kind" "page". See .Site.Pages.
```
**<span id="jump">.Site.Sections</span>**
```
top-level directories of the site.
```
**.Site.Taxonomies**
```
the taxonomies for the entire site. Replaces the now-obsolete .Site.Indexes since v0.11. Also see section Taxonomies elsewhere.
```
**.Site.Title**
```
a string representing the title of the site.
```