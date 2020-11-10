# How different are different core themes in drupal

While theme development you may have come across many Drupal core themes let's try to understand each one and where to use what.

### Bartik
Let's start with the first theme which we see after installing a drupal theme that is `Bartik`. Bartik is a responsive mobile-first theme that is used as the default theme for the drupal website it has many regions where content can be placed. When you open the `bartik.info.yml` file you can see a lot of attributes like the list of various regions for a page, a list of libraries and stylesheets used by the theme, etc. Bartik can be a good option if you want to quickly start building a website by making a few changes in colors and placing content in different regions.

### Seven

Seven is the default administrative theme for drupal it contains few regions place administrative menus and content and provide a clean and UI for the administrative pages. You can use Seven as a base theme if you want to create a theme for pages with a lot of configurations and settings.

Both Bartik and Seven are not backward compatible.


### Stark 

Stark is only used for demonstrating how your site will look with minimal markup and styling or for sites that have very strict markup and semantic requirements. Stark does not define any regions and does not contain any template files, hence if you want to use Stark as a base theme you will have to write custom code for each of drupal's template, which will take lots of efforts hence it is not a good idea to use Stark as a base theme. However Stark can be extremely useful for finding markup and CSS related bugs.


### Stable

Stable primarily serves as a backward compatibility layer, if any theme has a base theme set to `false` drupal will by default use stable as its base theme. Stables contain a copy of markup provided by drupal's `system` module. If you want to have full control over the markup and styling you should use stable as the base theme.


### Classy

Classy provides a handful of markup and styling capabilities which are enough to quickly get started with the theme development, both Bartik and seven themes are based on Classy.
If you are looking for a quick start for building a custom theme and do not require very heavy customization you should use Class as the base theme.


## References
[Theme Drupal Sites](https://drupalize.me/guide/theme-drupal-sites)
