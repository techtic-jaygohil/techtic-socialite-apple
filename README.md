# techtic-socialite-apple
SocialiteLogin - Apple

-----------------------------------

config\app.php

'providers' => [
    //....
    \SocialiteProviders\Manager\ServiceProvider::class, // add
    //....
];

-----------------------------------

app/Providers/EventServiceProvider

protected $listen = [
    \SocialiteProviders\Manager\SocialiteWasCalled::class => [
        // add your listeners (aka providers) here
        'SocialiteProviders\\Apple\\AppleExtendSocialite@handle',
    ],
];

-----------------------------------

config\app.php

    "apple" => [
        "client_id"     => env('APPLE_client_id'),
        "client_secret" => env('APPLE_client_secret'),
        'redirect'      => env('APPLE_redirect'),
    ],

-----------------------------------

// authorize with provider
return Socialite::with('apple')->redirect();

// fetch user after callback
$user = Socialite::with('apple')->user();

// fetch user using token ( token from apple authentication )
$token = "***************";
$user = Socialite::with('apple')->userFromToken($token));

-----------------------------------
