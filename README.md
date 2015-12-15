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
BMB requires both jQuery(1.7 or higher) and Bootstrap(3+) scripts be included in the DOM. We recommend placing at the end of <body/> element.

```html 
<!--  jQuery 1.7+  -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/1.11.3/jquery.min.map"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/1.11.3/jquery.min.map"></script>
<script src="/path/to/your/bootstrap-modal-build.js"></script>
```

### 2. Boostrap-Modal-Builder elements
The Modal Builder has two methods. 

The first method is used to build the modal and requires an object that holds the title [string] and content [array] which is an array of elements. This method is fairly simple and is all that is needed to build the dynamic modal.
 
The second method is a helper for building form elements into the modal content. There are a lot of options and it is does require some time to go through the method.
 
The following examples should help you understand how to quickly create a temporary modal dynamically.

```javascript
$(function(){
	// triggers dynamic modal on button with class hello-modal
	$('.hello-modal').on('click', function(ev) {
		ev.preventDefault();
		// we need obj.modalTitle and an obj.modalContent [an array] to build this properly
		var modalObj = {},
		modalObj.modalTitle='Hello Modal',
		$modalBody=$('<div></div>').addClass('modal-body'),
		$modalFooter=$('<div></div>').addClass('modal-footer').html('<button type="button" class="btn btn-link" data-dismiss="modal"><i class="fa fa-times"></i> Close</button>');
		// add some content to $modalBody;
		$modalBody.html('<h6>Hello World</h6><p>"One day you will wake up and there won''t be any more time to do the things you''ve always wanted. Do it now.” -Paulo Coelho<p>');
		// finish modalObj
		modalObj.modalContent=[$modalBody,$modalFooter];
		ALBA.ModalBuilder.buildModal(modalObj);
	}
});
```

Here is a more advanced example using the second method to add form elements into a form in the modal. Please see the documentation provided at [Bootstrap Modal Buileder](http://andrewalba.github.io/bootstrap-modal-builder)

```javascript
$(function(){
	// triggers dynamic modal on button with class form-modal
	$('.form-modal').on('click', function(ev) {
		ev.preventDefault();
		// we need obj.modalTitle and an obj.modalContent [an array] to build this properly
		var modalObj={},
			$modalBody=$('<div></div>').addClass('modal-body clearfix'),
			$modalForm=$('<form></form>').attr({method:'post',action:'/sendEmail',id:'contactForm',role:'form',autofocus:'full-name'}),
			$modalFooter=$('<div></div>').addClass('modal-footer').html(
			'<input type="hidden" name="subject" value="My Form Submission"/>' +
			'<button type="button" class="btn btn-link" data-dismiss="modal"><i class="glyphicon glyphicon-remove"></i> Close</button>'
			),
			$modalSubmit=$('<button></button>').attr({type:'submit',form:'contactForm'}).addClass('btn btn-primary').on('click', function(ev) {
				ev.preventDefault();
				$modalForm.submit();
				return false;
			}).html('<i class="fa fa-send"></i> Send'),
			modalObj.modalTitle='My Form';
		$modalFooter.prepend($modalSubmit);
		$modalBody.append(ALBA.ModalBuilder.buildModalFormElements({elAttr:{id:'full-name',name:'full-name',required:true,placeholder:'Your Full Name'},elClass:'form-control',label:{id:'full-name',html:'Full Name:'}}));
		$modalBody.append(ALBA.ModalBuilder.buildModalFormElements({inputType:'email',elAttr:{id:'from-email',name:'from-email',required:true,placeholder:'Your Valid Email'},elClass:'form-control',label:{id:'from-email',html:'Email Address:'}}));
		$modalBody.append(ALBA.ModalBuilder.buildModalFormElements({inputType:'textarea',elAttr:{id:'message-text',name:'message-text',required:false,placeholder:'Your Message'},elClass:'form-control',label:{id:'message-text',html:'Message:'}}));
		$modalForm.append($modalBody).append($modalFooter);
		modalObj.modalContent=[$modalForm];
		ALBA.ModalBuilder.buildModal(modalObj);
	}
});
```

License
------------
The MIT License (MIT)