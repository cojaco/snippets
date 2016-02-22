# snippets

## CSS
[Scalable and responsive embeded videos](#scalable-and-responsive-embeded-videos)

[Center Content](#center-content)

[Zoom layout](#zoom-layout)

[Responsive Patterns](#responsive-patterns)

## Javascript
[Crossbrowser viewport width](#crossbrowser-viewport-width)

[Crossbrowser responsive imageges](#crossbrowser-responsive-imageges)

[ios triggering resize events by scrolling] (#ios-triggering-resize-events-by-scrolling)

[Importing CSS Breakpoints Into Javascript] (#importing-css-breakpoints-into-javascrip)

[Remove/add value onfocus/onblur if empty in jquery, input field] (#remove-add-value-onfocus-onblur-if-empty-in-jquery-input-field)


## Magento
[Call snippets and pass variables-in-magento](#call-snippets-and-pass-variables-in-magento)

[Call custom variables](#call-custom-variables)

[Call blocks with ifconfig](#call-blocks-with-ifconfig)

[Find and call $this](#find-and-call-this)


##Processwire
[Frontendlogin resources](#frontendlogin-resources)



### Zoom layout
Note if you zoom a container with transform: scale(0.2); the Parents height needs to be set to the new height or you can try to set it to 0.
eg:
```css
html {height: 0; min-height:0; }
body {transform: scale(0.2);}
```
should work for IE9+

If you need to do this kind of stuff in older IEs try css property zoom.


Responsive Patterns

### Scalable and responsive embeded videos
```html
<div class="video-wrap">
    <iframe src="https://player.vimeo.com/video/1084537?color=ffffff&amp;title=0&amp;byline=0&amp;portrait=0" width="500" height="281" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
</div>

<style>
.video-wrap {
position: relative;
padding-bottom: 56.2%;
height: 0;
}
.video-wrap iframe {
position: absolute;
top: 0;
left: 0;
width: 100%;
height: 100%;
}
</style>
```
[Demo](http://htmlpreview.github.io/?https://github.com/cojaco/snippets/blob/master/html/video-wrap.html)

-------------------


###Center Content
```html
<div class="height-box">
    <div class="height-box-value"></div>
    <div class="height-content">
        <!-- make vertikal align -->
        <div class="v-align-block-wrapper">
            <div class="v-align-block">
                <div class="v-align-block-fallback">

                    <h2>title</h2>
                    <p>Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut
                    labore et dolore magna aliquyam erat, sed diam voluptua.
                    At vero eos et accusam et justo duo dolores et ea rebum.</p>

                </div>
            </div>

        </div>
    </div>
    <!-- make height -->
</div>

<style>

   /*  set height  */

    .height-box{
        position: relative;
        width: 100%;
        overflow: hidden;
    }
    .height-box-value {
        content: "";
        display: block;
        padding-top: 50%; /* height relative to container width*/
    }
    .height-content{
        position:  absolute;
        top: 0;
        left: 0;
        bottom: 0;
        right: 0;
        color: white;
        text-align: center;
        background: #333;
        color: #fff;
        background-size: cover;
    }

    /* center vertical */
    .v-align-block-wrapper {
        display: table;
        overflow: hidden;
        margin-left: auto;
        margin-right: auto;
        height: 100%;
        *position: relative;
        text-align: left;
    }

    .v-align-block {
        display: table-cell;
        vertical-align: middle;
        *position: absolute;
        *top: 50%;

    }

    .v-align-block-fallback {
        *position: relative;
        *top: -50%;
        padding: 0 10%;
        text-align: center;
        }

</style>
```
[Demo](http://htmlpreview.github.io/?https://github.com/cojaco/snippets/blob/master/html/center-box.html)

-------------------
## Javascript / Jquery

### Crossbrowser Viewport width

embed /javascript/viewportSize-min.js

```html
<script type="text/javascript">
    var width = viewportSize.getWidth();
    var height = viewportSize.getHeight();
</script>
```

Original: https://github.com/tysonmatanich/viewportSize

-------------------

### Crossbrowser responsive imageges  

```html
<picture>
  <source srcset="examples/images/extralarge.jpg" media="(min-width: 1000px)">
  <source srcset="examples/images/art-large.jpg" media="(min-width: 800px)">
  <img srcset="examples/images/art-medium.jpg" alt="…">
</picture>
```

Project Site: http://scottjehl.github.io/picturefill/  
Github: https://github.com/scottjehl/picturefill  

-------------------

### ios triggering resize events by scrolling

```js
jQuery(document).ready(function($) {

    // Store the window width
    var windowWidth = $(window).width();
    // or var windowWidth = viewportSize.getWidth(); if you use the plugin from above

    // Resize Event
    $(window).resize(function(){

        // Check window width has actually changed and it's not just iOS triggering a resize event on scroll
        if ($(window).width() != windowWidth) {

            // Update the window width for next time
            windowWidth = $(window).width();

            // Do stuff here

        }

        // Otherwise do nothing

    });

});
```

Original: http://stackoverflow.com/a/24212316

-------------------

### Remove/add value onfocus/onblur if empty in jquery, input field

####Html
```html
<input id="email" name="email" type="text" value="Write your email here" />
```


####Jquery
```js
$('#email')
  .on('focus', function(){
      var $this = $(this);
      if($this.val() == 'Write your email here'){
          $this.val('');
      }
  })
  .on('blur', function(){
      var $this = $(this);
      if($this.val() == ''){
          $this.val('Write your email here');
      }
  });​
```

Original: http://stackoverflow.com/questions/7377571/remove-add-value-onfocus-onblur-if-empty-in-jquery-input-field

Demo: http://jsfiddle.net/Shef/aujqU/

-------------------



### Importing CSS Breakpoints Into Javascript

Interessting concept

http://codepen.io/mherchel/pen/gbygBd

-------------------
## Magento

### Call snippets and pass variables in Magento
```php
<?php $type = $this->getTyp(); ?>
<?php $id = $this->getId(); ?>
<?php $height = $this->getHeight(); ?>
<?php $mtop = $this->getMtop(); ?>
<?php $mbottom = $this->getMbottom(); ?>
<?php $bg = $this->getBg(); ?>


<?php if ($type == 'help'): ?>
    <pre style="text-align: left"><?php echo $help; ?></pre>
<?php else: ?>

    <?php if (!$id): ?>
        <pre style="text-align: center">
    <?php echo 'video Id is missing' ?>
</pre>
    <?php endif ?>

    <?php if ($height): ?>
        <?php $styleHeight = 'padding-bottom: ' . $height . ';'; ?>
    <?php else: ?>
        <pre style="text-align: center">
<?php echo 'height is missing'; ?>
</pre>
    <?php endif; ?>
    <?php if ($mtop): ?>
        <?php $styleMtop = 'margin-top: ' . $mtop . ';'; ?>
    <?php endif; ?>
    <?php if ($mbottom): ?>
        <?php $styleMbottom = 'margin-bottom: ' . $mbottom . ';'; ?>
    <?php endif; ?>
    <?php if ($bg): ?>
        <?php $styleBg = 'background: ' . $bg . ';'; ?>
    <?php endif; ?>


    <?php if ($id && $height): ?>

        <div class="videoWrapper" style="<?php echo $styleHeight . $styleMtop . $styleMbottom . $styleBg ?>">
            <iframe src="https://player.vimeo.com/video/<?php echo $id ?>?title=0&amp;byline=0&amp;portrait=0" width="100%"
                    height="100%" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
        </div>

    <?php endif; ?>
<?php endif; ?>
```
Call the Snippet: {{block type="core/template" id="1084537" height="56.2%" mbottom="220px" bg="#fff" mtop="0px" template="snippets/fullwidthvid.phtml"  }}

-------------------

### Call custom variables

Plain Value per Store
```php
<?php
$value = Mage::getModel('core/variable')
    ->setStoreId(Mage::app()->getStore()->getId())
    ->loadByCode('variable_code')
    ->getValue('text');
?>
```
Html Value per Store
```php
<?php
$value = Mage::getModel('core/variable')
    ->setStoreId(Mage::app()->getStore()->getId())
    ->loadByCode('variable_code')
    ->getValue('html');
?>
```

http://stackoverflow.com/a/6222511

-------------------

### Call blocks with ifconfig

```xml
<block type="core/template" name="the.name">
            <action method="setTemplate" ifconfig="module/general/enable">
                <template>snippets/your_snippet.phtml</template>
            </action>
        </block>
```



-------------------

### Find and call $this

e.g. in media.phtml
```php
print_r(get_class($this));
```

Than in a new phtml you can go like this:
```php
$mediathis = new Mage_Catalog_Block_Product_View_Media();
```



-------------------
## Processwire

### Frontendlogin resources
Frontend Login:
https://processwire.com/talk/topic/1716-integrating-a-member-visitor-login-form/#entry15919
Module: FrontendUser:
http://modules.processwire.com/modules/frontend-user/
https://processwire.com/talk/topic/9811-frontenduser-login-logout-and-register-users-members/

Restrict User from Backend View
https://processwire.com/talk/topic/11122-delete-and-edit-pages-via-api/#entry104072
