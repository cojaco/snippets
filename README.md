# snippets

## CSS
[Scalable and responsive embeded videos](#scalable-and-responsive-embeded-videos)
[Center Content](#center-content)

## Magento
[Call snippets and pass variables](#call-snippets-and-pass-variables)


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
    }

</style>
```
[Demo](http://htmlpreview.github.io/?https://github.com/cojaco/snippets/blob/master/html/center-box.html)

-------------------

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

### Call snippets and pass variables
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
    <?php echo 'video Id fehlt' ?>
</pre>
    <?php endif ?>

    <?php if ($height): ?>
        <?php $styleHeight = 'padding-bottom: ' . $height . ';'; ?>
    <?php else: ?>
        <pre style="text-align: center">
<?php echo 'höhenangabe für Video fehlt'; ?>
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


