Bootstrap-wordpress-pagination
==============================

**A custom WordPress numbered pagination function to fully implement the [Bootstrap 3.x](http://getbootstrap.com/) pagination/pager style in a custom theme.**

* Original Autor URI: [OOPThemes](http://oopthemes.com/)
* Forum: [OOPThemes Discussio](http://oopthemes.com/forums/forum/themes-forum/)

Forked for Aquanotes wordpress theme with some more options
* Original Autor URI: [RedefineLab Ltd](http://redefinelab.com/)

Featured
--------
* Bootstrap Styling
* First & Last Buttoon
* Next & Previous Button
* Glyphicon can be added instead of Next & Pervious values
* Filter to overwrite values

How it Looks
------------

Below is the example of the Bootstrap WordPress Pagination. You can customize it with your own CSS styling.
![Extras](http://3.bp.blogspot.com/-XULxjp0E4uQ/U3Dyph_GJ9I/AAAAAAAABto/4rrOgV_D_Zw/s1600/pagination-wordpress-bootstrap.png)

installing Bootstrap WordPress Pagination
------------
Place **wp_bootstrap_pagination.php** in your WordPress theme folder `/wp-content/your-theme/`

Open your WordPress themes **functions.php** file  `/wp-content/your-theme/functions.php` and add the following code:

```php
// Register Custom Navigation Walker
require_once('wp_bootstrap_pagination.php');
```

or simply open the **wp_bootstrap_pagination.php** copy all the code and paste it in your themes **functions.php** file

Using Bootstrap WordPress Pagination
------------
Update your **index.php** or **template-blog.php** or any other file where you want to show the pagination. Add the below code into the file to show the Bootstrap WordPress Pagination.

```php
<?php
  if ( function_exists('wp_bootstrap_pagination') )
    wp_bootstrap_pagination();
?>
```
if pagination is not showing, go to WordPress Dashboard > Reading > Blog pages show at most > set value smaller then number of posts your blog has.

Filtering Next, Previous, First & Last with show/hide first and last links
-------------------------
To filter next and previous values use the following snippet into **functions.php**
```
function customize_wp_bootstrap_pagination($args) {
    $args['range'] = 4;
    $args['custom_query'] = FALSE;
    $args['show_first'] = FALSE;
    $args['show_last'] = FALSE;
    $args['first_string'] = 'First';
    $args['last_string'] = 'Last';
    $args['previous_string'] = '<span aria-hidden="true"><i class="fa fa-chevron-left" aria-hidden="true"></i></span>';
    $args['next_string'] = '<span aria-hidden="true"><i class="fa fa-chevron-right" aria-hidden="true"></i></span>';
    $args['before_output'] = '<nav aria-label="Page navigation"><ul class="pagination">';
    $args['after_output'] = '</ul></nav>';
    
    return $args;
}
add_filter('wp_bootstrap_pagination_defaults', 'customize_wp_bootstrap_pagination');
```
