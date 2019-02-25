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
* 定义kind字段，value值为：[{{ .Kind }}](#span.page.variables.kind)
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
**.Site.Sections**
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

##### Page Variables
使用方式
```
{{ $.Site.Params.author }}
{{ $.Site.Params.description }}
```
![](/mdfile/images/site-variables-config.png)
----

**.AlternativeOutputFormats**
```
contains all alternative formats for a given page; this variable is especially useful link rel list in your site’s <head>. (See Output Formats.)
```
**.Content**
```
the content itself, defined below the front matter.
```
**.Data**
```
the data specific to this type of page.
```
**.Date**
```
the date associated with the page; .Date pulls from the date field in a content’s front matter. See also .ExpiryDate, .PublishDate, and .Lastmod.
```
**.Description**
```
the description for the page.
```
**.Dir**
```
the path of the folder containing this content file. The path is relative to the content folder.
```
**.Draft**
```
a boolean, true if the content is marked as a draft in the front matter.
```
**.ExpiryDate**
```
the date on which the content is scheduled to expire; .ExpiryDate pulls from the expirydate field in a content’s front matter. See also .PublishDate, .Date, and .Lastmod.
```
**.File**
```
filesystem-related data for this content file. See also File Variables.
```
**.FuzzyWordCount**
```
the approximate number of words in the content.
```
**.Hugo**
```
see Hugo Variables.
```
**.IsHome**
```
true in the context of the homepage.
```
**.IsNode**
```
always false for regular content pages.
```
**.IsPage**
```
always true for regular content pages.
```
**.IsTranslated**
```
true if there are translations to display.
```
**.Keywords**
```
the meta keywords for the content.
```
**<span id="span.page.variables.kind">.Kind</span>**
```
the page’s kind. Possible return values are page, home, section, taxonomy, or taxonomyTerm. Note that there are also RSS, sitemap, robotsTXT, and 404 kinds, but these are only available during the rendering of each of these respective page’s kind and therefore not available in any of the Pages collections.
```
**.Language**
```
a language object that points to the language’s definition in the site config.
```
**.Lastmod**
```
the date the content was last modified. .Lastmod pulls from the lastmod field in a content’s front matter.
```
* If lastmod is not set, and .GitInfo feature is disabled, the front matter date field will be used.
* If lastmod is not set, and .GitInfo feature is enabled, .GitInfo.AuthorDate will be used instead.

__See also .ExpiryDate, .Date, .PublishDate, and .GitInfo.__

**.LinkTitle**
```
access when creating links to the content. If set, Hugo will use the linktitle from the front matter before title.
```
**.Next (deprecated)**
```
In older Hugo versions this pointer went the wrong direction. Please use .PrevPage instead.
```
**.NextPage**
```
Pointer to the next regular page (sorted by Hugo’s default sort). Example: {{if .NextPage}}{{.NextPage.Permalink}}{{end}}.
```
**.NextInSection**
```
Pointer to the next regular page within the same section. Pages are sorted by Hugo’s default sort. Example: {{if .NextInSection}}{{.NextInSection.Permalink}}{{end}}.
```
**.OutputFormats**
```
contains all formats, including the current format, for a given page. Can be combined the with .Get function to grab a specific format. (See Output Formats.)
```
**.Pages**
```
 .Site.Pages ,暂时不知区别
a collection of associated pages. This value will be nil within the context of regular content pages. See .Pages.
```
**.Permalink**
```
the Permanent link for this page; see Permalinks
```
**.Plain**
```
the Page content stripped of HTML tags and presented as a string.
```
**.PlainWords**
```
the Page content stripped of HTML as a []string using Go’s strings.Fields to split .Plain into a slice.
```
**.Prev (deprecated)**
```
In older Hugo versions this pointer went the wrong direction. Please use .NextPage instead.
```
**.PrevPage**
```
Pointer to the previous regular page (sorted by Hugo’s default sort). Example: {{if .PrevPage}}{{.PrevPage.Permalink}}{{end}}.
```
**.PrevInSection**
```
Pointer to the previous regular page within the same section. Pages are sorted by Hugo’s default sort. Example: {{if .PrevInSection}}{{.PrevInSection.Permalink}}{{end}}.
```
**.PublishDate**
```
the date on which the content was or will be published; .Publishdate pulls from the publishdate field in a content’s front matter. See also .ExpiryDate, .Date, and .Lastmod.
```
**.RSSLink**
```
link to the taxonomies’ RSS link.
```
**.RawContent**
```
raw markdown content without the front matter. Useful with remarkjs.com
```
**.ReadingTime**
```
the estimated time, in minutes, it takes to read the content.
```
**.Ref**
```
returns the permalink for a given reference (e.g., .Ref "sample.md"). .Ref does not handle in-page fragments correctly. See Cross References.
```
**.RelPermalink**
```
the relative permanent link for this page.
```
**.RelRef**
```
returns the relative permalink for a given reference (e.g., RelRef "sample.md"). .RelRef does not handle in-page fragments correctly. See Cross References.
```
**.Site**
```
see Site Variables.
```
**.Sites**
```
returns all sites (languages). A typical use case would be to link back to the main language: <a href="{{ .Sites.First.Home.RelPermalink }}">...</a>.
```
**.Sites.First**
```
returns the site for the first language. If this is not a multilingual setup, it will return itself.
```
**.Summary**
```
a generated summary of the content for easily showing a snippet in a summary view. The breakpoint can be set manually by inserting <!--more--> at the appropriate place in the content page. See Content Summaries for more details.
```
**.TableOfContents**
```
the rendered table of contents for the page.
```
**.Title**
```
the title for this page.
```
**.Translations**
```
a list of translated versions of the current page. See Multilingual Mode for more information.
```
**.Truncated**
```
a boolean, true if the .Summary is truncated. Useful for showing a “Read more…” link only when necessary. See Summaries for more information.
```
**.Type**
```
the content type of the content (e.g., posts).
```
**.UniqueID**
```
the MD5-checksum of the content file’s path.
```
**.Weight**
```
assigned weight (in the front matter) to this content, used in sorting.
```
**.WordCount**
```
the number of words in the content.
Section Variables and Methods 
Also see Sections.
```
**.CurrentSection**
```
The page’s current section. The value can be the page itself if it is a section or the homepage.
```
**.InSection $anotherPage**
```
Whether the given page is in the current section. Note that this will always return false for pages that are not either regular, home or section pages.
```
**.IsAncestor $anotherPage**
```
Whether the current page is an ancestor of the given page. Note that this method is not relevant for taxonomy lists and taxonomy terms pages.
```
**.IsDescendant $anotherPage**
```
Whether the current page is a descendant of the given page. Note that this method is not relevant for taxonomy lists and taxonomy terms pages.
```
**.Parent**
```
A section’s parent section or a page’s section.
```
**.Section**
```
The section this content belongs to. Note: For nested sections, this is the first path element in the directory, for example, /blog/funny/mypost/ => blog.
```
**.Sections**
```
The sections below this content.
```