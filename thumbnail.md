## Create Thumbnail

- Create functions.php

```
add_theme_support( 'post-thumbnails' );
set_post_thumbnail_size( 1568, 9999 );
```

- For showing

```
<?php if ( has_post_thumbnail() ) : ?>
  <a href="<?php the_permalink(); ?>" title="<?php the_title_attribute(); ?>">
  <img class="w-100" src="<?php the_post_thumbnail_url(); ?>"/>
  </a>
<?php endif; ?>
```
