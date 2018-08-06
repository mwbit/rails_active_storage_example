# Example: Active Storage

This is a little example to use the active storage in rails 5.2

## Instructions

1) Create a rails app: 
   rails new active_storage_example

2) Generate a scaffold
   rails generate scaffold title body:text   

3) Create db and run migrations
   rails db:create db:migrate

4) Install active storage and run db:migrate
   rails active_storage:install 
   rails db:migrate

5) insert in model post:
    has_one_attached :image

6) In posts_controller alter the method post_params to:
    params.require(:post).permit(:title, :body, :image)

7) In the view _form.html.erb alter the first line to:
   <%= form_with(model: post, local: true, multipart: true) do |form| %>

8) In the view _form.html.erb alter insert this code before form.submit:

    <div class="field">
        <%= form.label :image %>
        <%= form.file_field :image %>
    </div>

9) in the view show.html.erb add:
    <%= image_tag @post.image %>

10) start the server and do the tests
    rails s
    
         


   