# Pelican theme for vorpal.se

This is the [pelican][] theme for [vorpal.se](vorpal.se).

Some parts of the code is based on the pelican default theme called "[notmyidea][]".

## License

This theme is distributed under [AGPL-3.0](LICENSE.md). However, it appears that
the parts that come from the [notmyidea][] theme have all sorts of various
licenses, which means that honestly I'm not quite sure about the legal status of
it all.

## Required Pelican plugins

The theme has special support for the following plugins: 

 * [neighbors](https://github.com/getpelican/pelican-plugins/tree/master/neighbors)
 * [pelican-toc](https://github.com/ingwinlu/pelican-toc)
 * [assets](https://github.com/getpelican/pelican-plugins/tree/master/assets)
 * [pelican-cite][cite] - See notes below!

### pelican-cite support
The pelican-cite support (currently) requires using my improved and fixed
[fork][cite]. Also the following configuration is required:  

```python
BIBLIOGRAPHY_START = '<section class="bibliography"><hr/><h1>Bibliography</h1>'
BIBLIOGRAPHY_END = '</section>'
```

## Variables

This theme uses some extra variables in pelicanconf.py compared to the base
variables in pelican:

Menu related:

 * `MENUITEMS` - Custom menu items to the start of the menu. A list of
   `('label', 'url')`.  
 * `DISPLAY_PAGES_ON_MENU` - Display certain pages on the menu. Need to be
   enabled on a per page basis as well by adding the meta-data
   `display_on_menu: True` to the file.
 * `DISPLAY_CATEGORIES_ON_MENU` - Should categories be displayed on the menu at
    the top (or links to the categories, tags and archive page instead)
    
Footer related:

 * `FOOTER_RIGHT` - HTML code to put in the right side footer
 * `SOCIAL` - A list of `('label', 'url')`. Fancy icons are supported for a few
   different sites.
 * `PRIVACY_POLICY_URL` - Relative path of privacy policy.

Content related:

 * `DISABLE_AUTHOR_LINKS` - Do not link author pages from articles. Useful with
   a single author.
 * `CATEGORY_NEIGHBORS` - Add links like "next/previous" in category to
   articles. This is in addition to next/previous article.

Disqus support: There are some variables for disqus support inherited from
[notmyidea][]. This is untested since I don't use it myself!

In addition URL variables for direct templates are used:

 * `CATEGORIES_URL`
 * `TAGS_URL`
 * `ARCHIVES_URL`

[pelican]: <https://docs.getpelican.com>
[notmyidea]: <https://github.com/getpelican/pelican/tree/master/pelican/themes/notmyidea>
[cite]: <https://github.com/VorpalBlade/pelican-cite>
