# Pelican theme for vorpal.se

This is the [pelican][] theme for [vorpal.se](https://vorpal.se).

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
 * [assets](https://github.com/getpelican/pelican-plugins/tree/master/assets) -
   See notes below!
 * [pelican-jsmath][]
 * [pelican-cite][cite] - See notes below!

### assets support

This depends on a new unreleased version of the `webassets` python package that
contains [this pull request](https://github.com/miracle2k/webassets/pull/521).

To install this version use the following command in your venv:
```
pip install git+https://github.com/VorpalBlade/webassets.git@sri_calculation
```

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
 * `MATH_SCRIPT_TYPE` - Type of math script to use for [pelican-jsmath][]. One
   of: `mathjax-cdn`, `katex-cdn`, `katex-local`

Disqus support: There are some variables for disqus support inherited from
[notmyidea][]. This is untested since I don't use it myself!

In addition URL variables for direct templates are used:

 * `CATEGORIES_URL`
 * `TAGS_URL`
 * `ARCHIVES_URL`

### Favicon support

The variable FAVICON is used to specify the details of the favicon. An example
is probably simplest in this case:
 
Assuming you have a directory in your contents root called `favicon` containing
 * `favicon.ico`
 * `icon.svg`
 * `icon-16.png` (a 16x16 icon)
 * ...
 * `icon-310.png` (a 310x310 icon)

then the following code in your pelicanconf.py would work:

```python
EXTRA_PATH_METADATA = {'favicon/favicon.ico': {'path': 'favicon.ico'}}
STATIC_PATHS = ['favicon']
FAVICON = {
    'ico': {'sizes': ['16x16', '24x24', '32x32', '48x48', '64x64']},
    'svg': {'path': 'favicon/icon.svg'},
    'png': {'base_path': 'favicon/icon-',
            'sizes': [196, 160, 128, 96, 64, 32, 16]},
    'touch': {'base_path': 'favicon/icon-',
              'sizes': [180, 152, 144, 120, 114, 76, 72, 60, 57]},
}
```

Note here that the favicon.ico is assumed to go into the root, all other icons
can go wherever you want (just adjust the paths). For the .ico you need to list
the sizes it contains.

[pelican]: <https://docs.getpelican.com>
[notmyidea]: <https://github.com/getpelican/pelican/tree/master/pelican/themes/notmyidea>
[cite]: <https://github.com/VorpalBlade/pelican-cite>
[pelican-jsmath]: <https://github.com/svenkreiss/pelican-jsmath>
