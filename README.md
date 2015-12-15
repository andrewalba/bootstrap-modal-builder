## Bootstrap Modal Builder ##
>v.1.0.0

jQuery script that helps dynamically build temporary Bootstrap 3 modal windows.
[Visit Bootstrap Modal Builder landing page](http://andrewalba.github.io/bootstrap-modal-builder)

###Features:
* Fast Setup

### Demos
See our demo:
* [Bootstrap Modal Buileder](http://andrewalba.github.io/bootstrap-modal-builder)
* More to follow

## How To Use ##

### 1. Load jQuery, Bootstrap and Bootstrap Modal Builder (BMB) files
BMB requires both jQuery(1.7 or higher) and Bootstrap(3+) scripts be included in the DOM

```html
<!-- Default Styles -->
<link rel="stylesheet" href="/path/to/mecheer.css">
 
<!--  jQuery 1.7+  -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/1.11.3/jquery.min.map"></script>
```
### 2. Setup your HTML
You don't need any special markup. All you need is to add a class to each container [eg. div.frizzle] that you will be floating so MECHEER can find it. We are using Twitter Bootstrap for our example.

```html
<div class="row">
	<div class="col-md-4 col-sm-4 col-xs-12 frizzle">
		<a href="#"><img src="http://placehold.it/640x480" alt="" class="img-responsive"/></a>
	</div>
	<div class="col-md-4 col-sm-4 col-xs-12 frizzle">
		<a href="#"><img src="http://placehold.it/600x400" alt="" class="img-responsive"/></a>
	</div>
	<div class="col-md-4 col-sm-4 col-xs-12 frizzle">
		<a href="#"><img src="http://placehold.it/380x220" alt="" class="img-responsive"/></a>
	</div>
	...
	<div class="col-md-4 col-sm-4 col-xs-12 frizzle">
		<a href="#"><img src="http://placehold.it/480x270" alt="" class="img-responsive"/></a>
	</div>
	<div class="col-md-4 col-sm-4 col-xs-12 frizzle">
		<a href="#"><img src="http://placehold.it/600x338" alt="" class="img-responsive"/></a>
	</div>
</div>
```
### 3. Call the MECHEER plugin
Just initialize the plugin using `$(window).load();` jQuery method and watch the rows resize.

```javascript
$(window).load(function() {
	$('.frizzle').mecheer();
});
```

License
------------
The MIT License (MIT)