Samples
=======



## Running the samples

### Setup environment variables

https://runkit.com/settings/environment

### Get id and name for an access_token's user

```js
var FB = require('fb');

FB.options({
    appId: process.env.FACEBOOK_APP_ID,
    appSecret: process.env.FACEBOOK_APP_SECRET,
    version: 'v2.8',
});

FB.api('me', {access_token: process.env.FACEBOOK_ACCESS_TOKEN}, function (res) {
    if(!res || res.error) {
        console.warn(!res ? 'error occurred' : res.error);
        return;
    }
    console.log(res.id);
    console.log(res.name);
});
```

### Debug an access_token
```js
var FB = require('fb');

FB.options({
    appId: process.env.FACEBOOK_APP_ID,
    appSecret: process.env.FACEBOOK_APP_SECRET,
    version: 'v2.8',
});

FB.api('/debug_token',
    {
        input_token: process.env.FACEBOOK_ACCESS_TOKEN,
        access_token: process.env.FACEBOOK_APP_ID+'|'+process.env.FACEBOOK_APP_SECRET,
    },
    function (res) {
        if(!res || res.error) {
            console.warn(!res ? 'error occurred' : res.error);
            return;
        }
        console.log(res.id);
        console.log(res.name);
    });
```