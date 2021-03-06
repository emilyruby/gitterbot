What if you have a lot of users posting *things* to your website? Maybe your users want to have a profile, or a wall, of the *things* they’ve posted, and they want to be able to share it with their friends with a url? You can do that, no biggie!

Let’s say you used 

	>> yo angular-fullstack:route wall

to generate a <a href="#">http://myapp.wherever.com/wall/</a> route for your users. You want a link to <a href="#">http://myapp.wherever.com/wall/someUsername</a> to show a specific user’s *things*.  
Browse to **/client/app/wall/wall.js** and notice that it detects what URL the user is requesting before acting on it:  

~~~javascript
$routeProvider.when('/wall', …
~~~
You can customize that path to catch when a user is trying to see a profile associated with a specific username like so:  

~~~javascript
$routeProvider.when('/wall/:username', …
~~~
The colon before "username" indicates that this is a variable, which is then passed to the *$routeParams* module. In **wall.controller.js**, include *$routeParams*:  

~~~javascript
.controller('WallCtrl', function ($scope, $routeParams) { …
~~~
Then later on in **wall.controller.js**, you can see what username was requested in the URL by referring to the variable generated by *$routeProvider* using something like  

~~~javascript
var wallOwner = $routeParams.username;
~~~

[PREVIOUS](https://github.com/FreeCodeCamp/FreeCodeCamp/wiki/Quick-tip:-keep-data-in-sync)
[NEXT](https://github.com/FreeCodeCamp/FreeCodeCamp/wiki/More-useful-APIs)