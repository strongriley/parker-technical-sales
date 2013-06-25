# So Simple Theme

Looking for a simple, responsive, theme for your Jekyll powered blog? Well look no further. Here be **So Simple Theme**, the followup to [**Minimal Mistakes**](http://mmistakes.github.io/so-simple-theme) --- by designer slash illustrator [Michael Rose](http://mademistakes).

## So Simple Theme is all about:

* Responsive templates. Looking good on mobile, tablet, and desktop.
* Gracefully degrading in older browsers. Compatible with Internet Explorer 8+ and all modern browsers. 
* Minimal embellishments and subtle animations. 
* Readable typography to make your words shine.
* Support for large images to call out your favorite posts.
* Simple and clear permalink structure[^1].
* Tags for [Open Graph](https://developers.facebook.com/docs/opengraph/) and [Twitter Cards](https://dev.twitter.com/docs/cards) for a better social sharing experience.

General notes and suggestions for customizing So Simple Theme.

## Basic Setup

1. [Install Jekyll](http://jekyllrb.com) if you haven't already.
2. Fork the [So Simple Theme repo](http://github.com/mmistakes/so-simple-theme/)
3. Make it your own and customize, customize, customize.

## [Preview the Theme](http://mmistakes.github.io/so-simple-theme)

``` bash
so-simple-theme/
├── _includes
|    ├── browser-upgrade.html  //prompt to upgrade browser on < IE8
|    ├── footer.html  //site footer
|    ├── head.html  //site head
|    ├── navigation.html //site navigation and masthead
|    └── scripts.html  //jQuery, plugins, GA, etc.
├── _layouts
|    ├── page.html  //page layout
|    └── post.html  //post layout
├── _posts
├── assets
|    ├── css  //preprocessed less styles. good idea to minify
|    ├── js
|    |   ├── main.js  //jQuery plugins and settings
|    |   └── vendor  //all 3rd party scripts
|    └── less 
├── images  //images for posts and pages
├── _config.yml  //Site options
├── about.md  //about page
├── articles.html  //lists all posts from latest to oldest
├── index.html  //homepage. lists 10 latest posts
└── tags.html  //lists all posts sorted by tag
```

## Customization

### _config.yml

Most of the variables found here are used in the .html files found in `_includes` if you need to add or remove anything. A good place to start would be to change the title, tagline, description, and url of your site. When working locally comment out `url` or else you will get a bunch of broken links because they are absolute and prefixed with `{{ site.url }}` in the various `_includes` and `_layouts`. Just remember to uncomment `url` when building for deployment or pushing to **gh-pages**...

#### Owner/Author Information

Change your name, and avatar photo (200x200 pixels or larger), email, and social networking urls. If you want to link to an external image on Gravatar or something similiar you'll need to edit the path in `head.html` since it assumes it is located in `\images`.

Including a link to your Google+ profile has the added benefit of displaying [Google Authorship](https://plus.google.com/authorship) in Google search results if you've went ahead and applied for it.

#### Google Analytics and Webmaster Tools

Your Google Analytics ID goes here along with meta tags for [Google Webmaster Tools](http://support.google.com/webmasters/bin/answer.py?hl=en&answer=35179) and [Bing Webmaster Tools](https://ssl.bing.com/webmaster/configure/verify/ownershi) site verification.

#### Top Navigation Links

Edit page/post titles and URLs to include in the site's navigation. If you want to add links to other sites you can hardcode them into `navigation.html`.

``` yaml
# sample top navigation links
links:
  - title: About Page
    url: /about
  - title: Articles
    url: /articles
  - title: Other Page
    url: /other-page
```

#### Other Stuff

The rest is just your average Jekyll config settings. Nothing too crazy here...

### _includes

For the most part you can leave these as is since the author/owner details are pulled from `_config.yml`. That said you'll probably want to customize the copyright stuff in `footer.html` to your liking.

### Adding Posts and Pages

There are two main content layouts: `post.html` (for posts) and `page.html` (for pages). Both have support for large **feature images** that span the full-width of the screen, and both are meant for text heavy blog posts (or articles). 

#### Feature Images

A good rule of thumb is to keep feature images nice and wide so you don't push the body text too far down. An image cropped around around 1024 x 256 pixels will keep file size down with an acceptable resolution for most devices. If you want to serve these images responsively I'd suggest looking at [Picturefill](https://github.com/scottjehl/picturefill) or [Adaptive Images](http://adaptive-images.com/).

The two layouts make the assumption that the feature images live in the *images* folder. To add a feature image to a post or page just include the filename in the front matter like so. 

``` yaml
image:
  feature: feature-image-filename.jpg
  thumb: thumbnail-image.jpg #keep it square 200x200 px is good
```

The large texture images used in *Minimal Mistakes* are from [Love Textures](http://lovetextures.com), probably a good idea to swap these out with your own photos...

#### Categories

In the sample `_posts` folder you may have noticed `category: articles` in the front matter. I like keeping all posts grouped in the same folder. If you decide to rename or add categories you will need to modify the permalink in `articles.md` along with the filename (if renaming).

For example. Say you want to group all your posts under `blog/` instead of `articles/`. In your post add `category: blog` to the front matter, rename or duplicate `articles.md` to `blog.md` and change the permalink in that file to `permalink: /blog/index.html`.

If done correctly `/blog` should be a page listing all the site's posts.

#### Post/Page Thumbnails for OG and Twitter Cards

Post and page thumbnails work the same way. These are used by [Open Graph](https://developers.facebook.com/docs/opengraph/) and [Twitter Cards](https://dev.twitter.com/docs/cards) meta tags found in `head.html`. If you don't assign a thumbnail the image you assigned to `site.owner.avatar` in `_config.yml will be used.

#### Videos

Video embeds are responsive and scale with the width of the main content block with the help of [FitVids](http://fitvidsjs.com/).

Not sure if this only effects Kramdown or if it's an issue with Markdown in general. But adding YouTube video embeds causes errors when building your Jekyll site. To fix add a space between the `<iframe>` tags and remove `allowfullscreen`. Example below:

``` html
<iframe width="560" height="315" src="http://www.youtube.com/embed/PWf4WUoMXwg" frameborder="0"> </iframe>
```

#### Twitter Cards

Twitter cards make it possible to attach images and post summaries to Tweets that link to your content. Summary Card meta tags have been added to `head.html` to support this, you just need to [validate and apply your domain](https://dev.twitter.com/docs/cards) to turn it on.

## Further Customization

To make things easier I use LESS to build So Simple Theme's stylesheets. If you want to make some minor cosmetic alterations, take a look at `variables.less` in `assets/less/`. Changing some of the following variables can help make the theme your own. Just compile `main.less` using your preprocessor of choice and off you go -- I like [CodeKit](http://incident57.com/codekit/) for OS X and [Prepros](http://alphapixels.com/prepros/) for Windows.

``` css
// Typography
// --------------------------------------------------
@base-font: 'source-sans-pro', sans-serif;
@heading-font: @base-font;
@caption-font: @base-font;
@code-font: 'source-code-pro', monospace;
@alt-font: 'volkorn', serif;

@doc-font-size: 16;
@doc-line-height: 24;

// Colors
// --------------------------------------------------
@body-color         : #ebebeb;
@text-color         : #333;
@base-color       : #343434;    
@comp-color       : spin(@base-color, 180); 
@border-color       : @base-color;
@white              : #fff;
@black              : #000;
@accent-color       : @black;
@link-color         : #343434;
```

## Questions?

Having a problem getting something to work or want to know why I setup something in a certain way? Ping me on Twitter [@mmistakes](http://twitter.com/mmistakes) or [file a GitHub Issue](https://github.com/mmistakes/so-simple-theme/issues/new).

## License

This theme is free and open source software, distributed under the [GNU General Public License](LICENSE) version 2 or later. So feel free to use this Jekyll theme on your site without linking back to me or using a disclaimer.

If you'd like to give me credit somewhere on your blog or tweet a shout out to [@mmistakes](https://twitter.com/mmistakes), that would be pretty sweet.