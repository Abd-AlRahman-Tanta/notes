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

# SMTP Send Email

- it is for sending messages via email
- **How to do it?**

1. I must have an email that it will sends the messages in project
2. i must enable 2 step verification in the email
3. then we search for app passwords
4. then we enter to app passwords and enter the app name we want
5. a password field will show....i must save this password in my note
6. we set up the .env settings with this:

```
MAIL_MAILER=smtp
MAIL_SCHEME=null
MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USERNAME=iamwhitebeard2@gmail.com //your email
MAIL_PASSWORD=fnlu qoya kmbx olzz //password you saved
MAIL_FROM_ADDRESS=iamwhitebeard2@gmail.com //your email
MAIL_FROM_NAME="Rasoah" //name you want
```

7. **php artisan make:mail MailName**
8. in controller we write:`Mail::to($email) -> send(new MailName($parameter we want to show in message));`
9. in the class we write a variable ..public $variable
10. in constructor we write the parameter we sent in the ()
11. then we set `$this -> ourVariable = $parameter;`
12. then we go to second function and type the blade page it will render the message
13. in the blade page we use {{$parameter}} directly

# How to make Auth with another table?

1. we go to auth.php in config..and do copy and paste the guards and providers.
2. Example:

```
  'guards' => [
    'web' => [
      'driver' => 'session',
      'provider' => 'users',
    ],
    'marketer' => [
      'driver' => 'session',
      'provider' => 'marketers'
    ],
  ],


    'providers' => [
    'users' => [
      'driver' => 'eloquent',
      'model' =>  App\Models\User::class,
    ],
    'marketers' => [
      'driver' => 'eloquent',
      'model' => Modules\MarketerModule\Models\MarketerModel::class,
    ],
  ],
```

3. we go to the model of second table and add extends Authenticable..we can copy it from User Model
   `use Illuminate\Foundation\Auth\User as Authenticatable;`
4. if we want to auth with certain table..we use Auth::guard("guard_name")->login or logout...

# LaravelLocalization Package:

1. it is a package to handle the change of locale in app.php in config..so i can switch language..
2. For Example:

```
Route::group([
  "prefix" => "/" . LaravelLocalization::setLocal()
] ,  function() {routes..});
```

3. `LaravelLocalization::setLocal()` gets the local from url and set it to locale and return it..
4. if url is /ar/test then it will set local to ar and return ar
5. so in backend we just need to chack what is `app() -> getLocal()` so we can change returned json.
6. ### Tips:

- we must use **Redirects Middlewares** so we can handle alot of things like:
- "localeSessionRedirect" => it store the current locale in the session..so if user navigates to "/test" ..this middleware will returned him to "/currentLocal/test"
- "localizationRedirect" => Ensures that every URL has a language prefix. If the user visits a route without /en or /ar, it redirects to the correct localized URL.

7. ### Helpers:

- `LaravelLocalization::localizeUrl('/test')` => // If current locale is Spanish, it returns `/es/test`
- `LaravelLocalization::getLocalizedURL('en')` => // Returns current url with English locale.
- `LaravelLocalization::getSupportedLocales()` => //get all supported locals
- `LaravelLocalization::getSupportedLanguagesKeys()` => //get all supported keys for locals
- `LaravelLocalization::getCurrentLocale()` => //Return the key of the current locale.

8. ### To change lang:
