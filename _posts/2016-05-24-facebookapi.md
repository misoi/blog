---
layout: post
title: How to integrate your website with a facebook account
---




Facebook API implementations usage has become so rampant nowadays in the world of software development.The Facebook API is the primary way to get data in and out of Facebook's platform. It's a low-level HTTP-based API that you can use to query data, post new stories, manage ads, upload photos and a variety of other tasks that an app might need to do.

Facebook API that are commonly used:-

1. Login Api

2. Comment Api

3. Graph Api and many more

4. sharing Api

5. messanger platform

Today am going to show you how to integrate your website with a facebook login Api.
At the end of this article you will have learn how to integrate and even login using your own facebook account.

---
Subtitle: Steps to be followed
---
Step1: Search for facebook developers page in the internet or use this link http//:developers.facebook.com and choose facebook login among others.
Step2: On clicking the facebook login, you will be redirected to a page with "the world's number one social login product", scroll down to where you will see "ADD LOGIN" and click on it.
step3: Choose websites or mobile websites on the next page. There you will have to login to facebook using your account, so unfortunate for those who don't have one but you can create one.You will be asked to input your email/username and password.
Step4: Upon loging in successfull, go to add new app and and choose website.
Step 5: Input your app name(any name you can easily remember) and enter your email on the modal window. For category choose any and create app id
step6: Take the code in the quick start page after choosing websitesor mobile website
 this code below 
 
  <!DOCTYPE html>

 <html>
<head>
<title>Facebook Login JavaScript Example</title>
<meta charset="UTF-8">
</head>
<body>
<script>
  // This is called with the results from from FB.getLoginStatus().
  function statusChangeCallback(response) {
    console.log('statusChangeCallback');
    console.log(response);
    // The response object is returned with a status field that lets the
    // app know the current login status of the person.
    // Full docs on the response object can be found in the documentation
    // for FB.getLoginStatus().
    if (response.status === 'connected') {
      // Logged into your app and Facebook.
      testAPI();
    } else if (response.status === 'not_authorized') {
      // The person is logged into Facebook, but not your app.
      document.getElementById('status').innerHTML = 'Please log ' +
        'into this app.';
    } else {
      // The person is not logged into Facebook, so we're not sure if
      // they are logged into this app or not.
      document.getElementById('status').innerHTML = 'Please log ' +
        'into Facebook.';
    }
  }

  // This function is called when someone finishes with the Login
  // Button.  See the onlogin handler attached to it in the sample
  // code below.
  function checkLoginState() {
    FB.getLoginStatus(function(response) {
      statusChangeCallback(response);
    });
  }

  window.fbAsyncInit = function() {
  FB.init({
    appId      : '{your-app-id}',# APP ID SHOULD BE ACCURATE AND SAME WITH THE ONE IN SCRIP.
    cookie     : true,  // enable cookies to allow the server to access 
                        // the session
    xfbml      : true,  // parse social plugins on this page
    version    : 'v2.5' // use graph api version 2.5
  });

  // Now that we've initialized the JavaScript SDK, we call 
  // FB.getLoginStatus().  This function gets the state of the
  // person visiting this page and can return one of three states to
  // the callback you provide.  They can be:
  //
  // 1. Logged into your app ('connected')
  // 2. Logged into Facebook, but not your app ('not_authorized')
  // 3. Not logged into Facebook and can't tell if they are logged into
  //    your app or not.
  //
  // These three cases are handled in the callback function.

  FB.getLoginStatus(function(response) {
    statusChangeCallback(response);
  });

  };

  // Load the SDK asynchronously
  (function(d, s, id) {
    var js, fjs = d.getElementsByTagName(s)[0];
    if (d.getElementById(id)) return;
    js = d.createElement(s); js.id = id;
    js.src = "//connect.facebook.net/en_US/sdk.js";
    fjs.parentNode.insertBefore(js, fjs);
  }(document, 'script', 'facebook-jssdk'));

  // Here we run a very simple test of the Graph API after login is
  // successful.  See statusChangeCallback() for when this call is made.
  function testAPI() {
    console.log('Welcome!  Fetching your information.... ');
    FB.api('/me', function(response) {
      console.log('Successful login for: ' + response.name);
      document.getElementById('status').innerHTML =
        'Thanks for logging in, ' + response.name + '!';
    });
  }
</script>

<!--
  Below we include the Login Button social plugin. This button uses
  the JavaScript SDK to present a graphical Login button that triggers
  the FB.login() function when clicked.
-->

<fb:login-button scope="public_profile,email" onlogin="checkLoginState();">
</fb:login-button>

<div id="status">
</div>

</body>
</html>

Also take the script given after creating an app id.Code like-:
<script>
  window.fbAsyncInit = function() {
    FB.init({
      appId      : '263251174027415',#VERY IMPORTANT WRITE THE CORRECT APP ID IT WILL GIVE YOU BIG ERRORS IF YOU DON'T 
      xfbml      : true,
      version    : 'v2.6'
    });
  };

  (function(d, s, id){
     var js, fjs = d.getElementsByTagName(s)[0];
     if (d.getElementById(id)) {return;}
     js = d.createElement(s); js.id = id;
     js.src = "//connect.facebook.net/en_US/sdk.js";
     fjs.parentNode.insertBefore(js, fjs);
   }(document, 'script', 'facebook-jssdk'));
</script>


Down there enter your website link and click next.

you will see test your facebook integration,at this point you can testit but you will see the "facebook login" icon after hosting your website and you will have killed it :-).

For more precise steps visit http://developers.facebook.com page and follow them one by one.

Thanks




