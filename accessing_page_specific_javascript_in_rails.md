# Accessing Page Specific Javascript in Rails


The Rails Asset Pipeline, which compiles all of the Javascript into a single "application.js" file, can be problematic when trying to implement page-specific Javascript.  Oftentimes, a variable which has been defined on one page will be undefined on another, rendering our code useless.  

Giving class names which reference the application controller and action to "body" tag element of each page is a convenient and simple solution I used in a recent project to utilize page-specific Javascript without undoing the Rails Asset Pipeline infrastructure.

Here are the main steps to making that happen:


1.  In the head of the HTML document, give the "body" tag a class name which references the controller and action contained in the parameters of the HTTP request being processed:

		%body{ class: "#{params[:controller] +"_"+ params[:action] }" }
		
	As an example, if we have a user model, the "user show" page's "body" tag will have the class "users_show".  This naming practice allows us to set up a conditional statement at the beginning of our javascript code, and to have code run only if the page's name matches the name we specify:
	
1.  Inside of our "/javascripts/users/show.js" file, we have 
	
		$(function() { // document.ready is important here!!
  			if($("body").hasClass("users_show")) {
  			// this is where all of our user-show page specific
  			// Javascript goes
  			}
  		})
  		
This way, our Javascript will be compiled into a single application.js file without breaking when we have  page-specific code to run.
	
	
	
	