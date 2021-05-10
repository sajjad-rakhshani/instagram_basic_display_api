# instagram_basic_display_api
first get start in facebook developers as https://developers.facebook.com/docs/instagram-basic-display-api/getting-started
i get instagram posts in php as below :
at first redirect user to this address to Authenticate user (do this every time):
```php
https://api.instagram.com/oauth/authorize?
  client_id=your_instagram_app_id
  &redirect_uri=redirect-uri
  &scope=user_profile,user_media
  &response_type=code
```
then user redirect to redirect-uri that you specify, then you can get users media as below:
```php
$client_id = 'your_instagram_app_id';
$client_secret ='your_instagram_app_secret';
$redirect_uri = 'redirect-uri';
$code = $_GET['code'];
$url = "https://api.instagram.com/oauth/access_token";
$access_token_parameters = array(
  'client_id'                =>     $client_id,
  'client_secret'            =>     $client_secret,
  'grant_type'               =>     'authorization_code',
  'redirect_uri'             =>     $redirect_uri,
  'code'                     =>     $code
);
```
