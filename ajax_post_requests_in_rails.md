# Ajax Post Requests in Rails

### *Completing asynchronous Javascript CRUD actions is easy with jQuery... Here's a 4 step guide to making posts without reloading the page (assuming your models/views/controllers are already set up).* 
<br>

1. Add a Javascript event listener to the form's submit action and prevent the form's default behavior (an HTTP post request) upon submission:  (the following is a user sign up route implemented using Ajax, ".new_user" is the class of the form element.)


		$( document ).ready( function() {
		  $(".new_user").submit( function(e) {
		    e.preventDefault();

2.  Instead make a post request using jQuery & include your model's parameters as arguments to be passed to the controller:	
		    
	    var $this = $(this);
   		var name = $this.find("#user_name").val();
   		var phone = $this.find("#user_phone").val();
	
		$.post('/users', { user: { name: name, phone: phone } } ) 
		
3.  In the controller layer, parse the incoming parameters and render the appropriate response as a json object (inside user_controller.rb): 

		def create
		    @user = User.new(user_params)
		
		    if @user.save
		      render json: { status: 'success' }
		    else
		      render json: { status: 'failure' }
		    end
		end
4.  Handle the response by updating the views appropriately: 	
		
		      .done(function(res) {
		        if(res.status == 'success') {
		          $("div.new-user-form")
		            .append("<div id='subscribed'><div class='arrow-left'></div><span>Woo hoo! You're subscribed!</span></div>")
		            .toggleClass('subscribed')
		        } else {
		          $("div.new-user-form").append("<span> Something went wrong </span>")
		        }
		      })
		  })
		})
Using Ajax to handle CRUD actions is helpful in streamlining the functionality of an app.  Having too many page reloads slows down the app and diminishes user experience.  It is important to get comfortable using jQuery/Ajax as a strategy in the development process.
	
