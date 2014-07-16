# What's in a Namespace?

**What's in a namespace and why would you use one in your Rails application?**

When building a web based application, such as an e-commerce site or a photo sharing app, what the user sees and interacts with is oftentimes just the surface level of a web application's full functionality.    Clients, who may or may not be technologically savvy, will often require an interface to control the content of a site. In Ruby on Rails, namespaces come in handy when building out administrative functionality for an app.


In the [Controller Namespaces and Routing](http://guides.rubyonrails.org/routing.html#controller-namespaces-and-routing) of the Ruby on Rails documentation, it reads, "You may wish to organize groups of controllers under a namespace. Most commonly, you might group a number of administrative controllers under an Admin:: namespace. You would place these controllers under the app/controllers/admin directory, and you can group them together in your router."  Conveniently, by placing the following, as an example, inside of your 'routes.rb' file:
	  
	  		namespace :admin do	  		
    			resources :users, :orders
    		end
As a result, Admin::Users Controller will have access to the following admin routes for users and orders controller.  	
    	
	    GET /admin/users	
		GET	/admin/users/new	
		POST	/admin/users	
		GET	/admin/users/:id	
		GET	/admin/users/:id/edit		
		PATCH/PUT	/admin/users/:id		
		DELETE	/admin/users/:id
		
We also have to define a subdirectory 'admin' within our controllers directory, and there define a 'users_controller.rb' as well as an 'orders_controller.rb', which inherits from 'Admin::ApplicationController" (application_controller.rb).  Namespaces are essentially reserved routes for functionality which is distinct from the main functionality of an app.
		
When working with admin namespaces, it is important to remember that these routes should not be accessible by common users.  For this reason, there will most likely have to be a SessionsController, as well as admin login (authorization and authentication) functionality.  Most web based applications built in Ruby on Rails will require admin functionality, at least the apps we make at DevShop do.  For this reason, it is important to gain an understanding of namespaces, what they do, and when they should be used.

