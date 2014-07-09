# Admin Functionality for your Rails Web Application

Oftentimes, when doing web based application development, your client might require administrative control, such as the ability to create, update, and delete, over the content of the site. Here are the steps I follow when implementing "admin" functionality in an app:

1.  Create an admin namespace, inside of 'routes.rb':
	- If you, for example, would like your administrator to be able to have access to CRUD actions over the "products" model, the namespace would look like:
	  
	  		namespace :admin do	  		
    			resources :products
    		end
    - The corresponding routes look like: 
	    	
		    admin_products GET    /admin/products(.:format)   admin/products#index
	                        POST   /admin/products(.:format)  admin/products#create
		    new_admin_product GET    /admin/products/new(.:format)   admin/products#new
		    edit_admin_product GET    /admin/products/:id/edit(.:format) admin/products#edit
	         
	        admin_product GET    /admin/products/:id(.:format)  admin/products#show
		                  PATCH  /admin/products/:id(.:format)   admin/products#update
		                  PUT    /admin/products/:id(.:format)   admin/products#update
		               	  DELETE /admin/products/:id(.:format)  admin/products#destroy
		
	- Conveniently, we now have access to routes over our "products" model only in the "admin" namespace, which will require a signing in and authentication to be accessed.
    	
1.  Generate an 'admin' model (rails g model admin email:string password_confirmation: string) & add "has_secure_password" to the 'admin.rb' file.  Implement admin authentication and authorization to access these admin pages.

1.  Create a specific "Admin::ApplicationController", which the "Admin::ProductsController" inherits from.

