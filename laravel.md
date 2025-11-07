# Helpers :

- its a function that written in one place and i can use it in any place i want!
- it usefull for DRY
- there is ready helpers from laravel in the documentation we can use
- **How to use?:**

1. ceate a .php file in app folder -> utilis
2. we write the function we wan to use inside the .php file
3. we must make the function in this file readable in any place in the project ..so we make it statc

# Logs :

1. it is og viewer that shows me everything happpen in the project
2. it is in storage/logs/laravel.log
3. if we want to log somthing in laravel log viewer we write inside the function : ` Log::static_method("message");`

### Note

- the static method is based on your status like:info,error,...
- we must install package for log to make it view in better way ...
- we can see the log in the url :`localhost:127.0.0.1/log-viewer`
- we can install it from first git hub link when search for log viewer laravel

### Most Segnifitic Log static methods :

```
Log::error()
Log::warning()
Log::info()
```

### How to use?

```
//this will save in log with info the message of attempt to auth
Log:info("attempt to auth" , ["auth_data" => $req -> only("name" , "email")]);
```

# Soft Delete

- it is something like recycle bin used to hide the thing from user based on delete but it still exist!
- **How to use?**

1. in the table of database we add column called `$table->softDeletes();`
2. this will create column called **deleted_at**
3. when the this is deleted...the deleted_at will has a value..and when he thing is not deleted...then the deleted_at is null..
4. laravel automaticlly handle this thing

- **Steps for soft delete**

1. in the model we write in the class out of any function `use softDeletes;`
2. then in the controller ..the delete to bin is the same regular delete method..
3. to get only trashed elements `Model::onlyTrashed -> get();`
4. to restore specific element `Model::onlyTrashed()->find($id) -> restore();`
5. to force delete element `Model::onlyTrashed()->find($id) -> forceDelete();`

# N+1 problem:

- its problem happens with queries on database for relation ship..
- when bring a one thing with all its relation ship in tow places sperated...it will request many quary for it..
- like if we have users..each user has many tasks..it is one to many relation.
- if we did :

```
$users = User::all();
foreach($users as $user) {
  echo $user -> tasks;
};
```

- this will request (do query) in times of users number length + 1.
- the +1 is for getting all users.

### Solution:

- we do instead get users with thier tasks:

```
$users = User::with("tasks") -> get();
```

# SMTP Send Email

- it is for sending messages via email
- How to do it?

1. I must have an email that it will sends the messages in project
2. i must enable 2 step verification in the email
3. then we search for app passwords
4. then we enter to app passwords and enter the app name we want
5. a password field will show....i must save this password in my note
6. we set up the .env settings with this:

MAIL_MAILER=smtp
MAIL_SCHEME=null
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME="iamwhitebeard2@gmail.com "//your email
MAIL_PASSWORD="fnlu qoya kmbx olzz" //password you saved
MAIL_FROM_ADDRESS="iamwhitebeard2@gmail.com" //your email
MAIL_FROM_NAME="Rasoah" //name you want

7. php artisan make:mail MailName
8. in controller we write:Mail::to($email) -> send(new MailName($parameter we want to show in message));
9. in the class we write a variable ..public $variable
10. in constructor we write the parameter we sent in the ()
11. then we set $this -> ourVariable = $parameter;
12. then we go to second function and type the blade page it will render the message
13. in the blade page we use {{$parameter}} directly
