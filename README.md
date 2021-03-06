# wordpress-theme-development
Wordpress theme development Mini-docs

## Create Theme

- Goto `/wp-content/themes` and create a folder with Theme name
- Include `style.css`

```
/*
Theme Name: Custom Wordpress Theme
Theme URI: https://wordpress.org/themes/twentyseventeen/
Author: Sanjay PJ
Author URI: https://wordpress.org/
Description: Twenty Seventeen brings your site to life with immersive featured images and subtle animations. With a focus on business sites, it features multiple sections on the front page as well as widgets, navigation and social menus, a logo, and more. Personalize its asymmetrical grid with a custom color scheme and showcase your multimedia content with post formats. Our default theme for 2017 works great in many languages, for any abilities, and on any device.
Version: 1.0
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html
Text Domain: twentyseventeen
Tags: one-column, two-columns, right-sidebar, flexible-header, accessibility-ready, custom-colors, custom-header, custom-menu, custom-logo, editor-style, featured-images, footer-widgets, post-formats, rtl-language-support, sticky-post, theme-options, threaded-comments, translation-ready
This theme, like WordPress, is licensed under the GPL.
Use it to make something cool, have fun, and share what you've learned with others.
*/
```
- Include `index.php`
- Activate theme on Dashboard

- Include `header.php`
- Use `<?php get_header(); ?>` to show it on index.php
- Include `footer.php`
- Use `<?php get_footer(); ?>` to show it on index.php
- To get theme uri `<?php echo get_template_directory_uri() ?>`

## Create Pages

- Include page.php

```
Page ID -> <?php the_ID(); ?> <br>
Page Heading -> <?php the_title(); ?> 
<?php
// TO SHOW THE PAGE CONTENTS
while ( have_posts() ) : the_post(); ?> <!--Because the_content() works only inside a WP Loop -->
    <div class="entry-content-page">
        <?php the_content(); ?> <!-- Page Content -->
    </div><!-- .entry-content-page -->

<?php
endwhile; //resetting the page loop
wp_reset_query(); //resetting the page query
?>
```

- To create new page templates `page-{slug}.php`

```
<?php
/*
Template Name: Full-width layout
?>
```

- And select template while creating pages
