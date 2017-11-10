# wp-theme-woocomerce
Wordpress theme extension base, to add Woocommerce support to the theme.

__Notice!__

__This package is not "ready from the box". Thus you will need to perform some file edits.__
	
__I recommend to add all changes to child-theme.__

## Edits to perform:

+ In __functions.php__ include base wrapper class.
	>
    >`locate_template( 'extensions/woocommerce/main.php', true );`
    >

+ Duplicate __header.php__ and __footer.php__ from original theme and rename them to __header-shop.php__ and __footer-shop.php__. You already have __sidebar-shop.php__ included.
	You may omit this step if you don't need the shop header and footer to differ from original site header and footer. Although you will still need copies of header and footer to integrate 'Shop menu'(see further).

+ Open your __index.php__, from original theme. Replace code inside __extensions/woocommerce/templates/template-shop.php__ with "loop code"(typically all between __get_header()__ and __get_footer()__).
	
    If __get_sidebar()__ is present inside "loop code" - replace it with __get_sidebar('shop')__.
	Alternatively you can replace __template-shop.php__ with renamed __index.php__. In this case, replace all occurrences of __get_header__, __get_footer__ and __get_sidebar__ calls whith their "shop" versions.
	
	This will provide you with static page template named 'Shop Template'. Available for selection in admin section of the site. On 'Edit Page' page, inside 'Page Attributes' meta-box.
	Main purpose of this template - output 'Shop Sidebar' on desired, non related to shop, pages.

+ Considering all performed well. Inside Admin area, you should see notice asking to perform requiered plugins instalation. Do install and activate plugins.

+ Install Woocommerce 'dummy data' (wp-content/plugins/woocommerce/dummy-data/dummy-data.xml), if needed.

+ Inside Admin area -> Appearance->Menus section, there will be added 'Shop menu' location. Create and attach new menu to it.

+ Now you can include __shop-nav-menu.php__-template
	>
	>`get_template_part( 'extensions/woocommerce/templates/shop-nav-menu' );`
	>

+ Add minicart navbar
	>
	>`get_template_part( 'extensions/woocommerce/templates/shopping-cart-link' );`
	>

+ Inside __extensions/woocommerce/assets/scss/__ you will find __styles.scss__ - adjust colors and rules to to suffice your needs. You may compile scss with __extensions/woocommerce/sass-watch.bat__ locally, if you have node.js and node-sass installed. Optionaly you can edit __extensions/woocommerce/assets/css/styles.css__.

## Check for bugs and gliches
Should add some tipical 'shit happens' examples here in future

## Files description(respectively to __extensions/woocommerce/__)
	- __main.php__ - main "wrapper" class.
	- __assets\css\styles.css__ - styles.
