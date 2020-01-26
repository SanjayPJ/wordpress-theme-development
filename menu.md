## Creating Menu

- Create functions.php

```
add_theme_support( 'menus' );

function wpb_custom_new_menu() {
  register_nav_menus(
    array(
      'main' => __( 'Main' ),
      'hello-there' => __( 'Hello There' )
    )
  );
}
add_action( 'init', 'wpb_custom_new_menu' );
```

- Goto Appearance > Menus > Menu Settings > Set current menu

- To Show

```
<?php

$parent = array();
$menu_name = 'main';
if (($locations = get_nav_menu_locations()) && isset($locations[$menu_name])) {
	$menu = wp_get_nav_menu_object($locations[$menu_name]);
	$menu_items = wp_get_nav_menu_items($menu->term_id);

	$parent_id = 0;

	foreach ((array) $menu_items as $key => $menu_item) {

		if ($menu_item->menu_item_parent == 0) {
			$parent_id = $menu_item->db_id;
			$title = $menu_item->title;
			$url = $menu_item->url;
			array_push($parent, array("title" => $title, "url" => $url, "child" => array()));
		} else if ($menu_item->menu_item_parent == $parent_id) {
			$title = $menu_item->title;
			$url = $menu_item->url;
			array_push($parent[count($parent) - 1]["child"], array("title" => $title, "url" => $url));
		} else {}
	}
}
?>

<ul class="nav mb-4">
<?php
foreach ($parent as $key => $value) {
	if (empty($value["child"])) {
		echo "<li class='nav-item'><a class='nav-link' href='" . $value["url"] . "'>" . $value["title"] . "</a></li>";
	}
}
?>
</ul>
```
