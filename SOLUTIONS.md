1. What controller and action handles the data from the form submission?

The 'tasks controller' uses the 'new' action.

2. What controller and action would be used if you did a GET request on the /users route?

The 'users controller' and the 'show' action.

3. Write out the step-by-step process that your rails application will take to render the tasks/new route.

Browser makes request to /tasks/new route, Rails routes to the 'new' action in the 'tasks controller'. The 'new' action asks 'tasks controller' to create a new @task variable which is passed to the view. Using embedded ruby, the view renders the 'new' page as HTML, and the Controller passes the rendered HTML to the browser.

4. What file is responsible for managing the mapping between your application and the tasks database table?

config/routes.rb

5. Explain all 7 of the RESTful actions in Rails
    List each action by its name
    Explain which HTTP verbs pair with each action
    Write a short sentence for each action that summarizes what it does

index - GET - returns a list of all of that type of resource

show - GET - returns the resource with the specified ID

new - GET - returns HTML form for making a new resource

edit - GET - returns HTML form to edit resource

create - POST - creates a new resource

update - PUT/PATCH - updates a resource

destroy - DELETE - deletes a resource


Creating Users with ruby server console:

>> first_user = User.create
   (1.2ms)  SELECT sqlite_version(*)
   (0.1ms)  begin transaction
  User Create (0.4ms)  INSERT INTO "users" ("created_at", "updated_at") VALUES (?, ?)  [["created_at", "2020-01-19 22:15:57.697228"], ["updated_at", "2020-01-19 22:15:57.697228"]]
   (0.7ms)  commit transaction
=> #<User id: 2, email: nil, active: nil, created_at: "2020-01-19 22:15:57", updated_at: "2020-01-19 22:15:57">
>> first_user.update(email: "phil.mac@email.com")
   (0.1ms)  begin transaction
  User Update (0.3ms)  UPDATE "users" SET "email" = ?, "updated_at" = ? WHERE "users"."id" = ?  [["email", "phil.mac@email.com"], ["updated_at", "2020-01-19 22:16:28.627131"], ["id", 2]]
   (0.9ms)  commit transaction
=> true
>> first_user.update(active: true)
   (0.1ms)  begin transaction
  User Update (0.5ms)  UPDATE "users" SET "active" = ?, "updated_at" = ? WHERE "users"."id" = ?  [["active", 1], ["updated_at", "2020-01-19 22:16:58.469087"], ["id", 2]]
   (1.2ms)  commit transaction
=> true
>> second_user = User.create
   (0.1ms)  begin transaction
  User Create (0.5ms)  INSERT INTO "users" ("created_at", "updated_at") VALUES (?, ?)  [["created_at", "2020-01-19 22:17:18.350740"], ["updated_at", "2020-01-19 22:17:18.350740"]]
   (1.3ms)  commit transaction
=> #<User id: 3, email: nil, active: nil, created_at: "2020-01-19 22:17:18", updated_at: "2020-01-19 22:17:18">
>> second_user.update(email:"bob@email.com")
   (0.1ms)  begin transaction
  User Update (0.4ms)  UPDATE "users" SET "email" = ?, "updated_at" = ? WHERE "users"."id" = ?  [["email", "bob@email.com"], ["updated_at", "2020-01-19 22:17:42.054045"], ["id", 3]]
   (0.9ms)  commit transaction
=> true
>> second_user.update(active: true)
   (0.1ms)  begin transaction
  User Update (0.5ms)  UPDATE "users" SET "active" = ?, "updated_at" = ? WHERE "users"."id" = ?  [["active", 1], ["updated_at", "2020-01-19 22:17:54.361815"], ["id", 3]]
   (3.1ms)  commit transaction
=> true