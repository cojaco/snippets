# snippets

## CSS
[Scalable and responsive embeded videos](scalable-and-responsive-embeded-videos)

### Scalable and responsive embeded videos
```html
<div class="video-wrap">
    <!-- Copy & Pasted from YouTube -->
    <iframe src="https://player.vimeo.com/video/1084537?color=ffffff&title=0&byline=0&portrait=0" width="500" height="281" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
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

