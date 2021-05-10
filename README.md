# instagram_basic_display_api
first get start in facebook developers as https://developers.facebook.com/docs/instagram-basic-display-api/getting-started
i get instagram posts in php as below :
at first redirect user to this address to Authenticate user (do this every time):
```ruby
https://api.instagram.com/oauth/authorize?
  client_id=your_app_id
  &redirect_uri=redirect-uri
  &scope=user_profile,user_media
  &response_type=code
```
then user redirect to redirect-uri that you specify, then you can get users media as below:
```php
$client_id = '221728789576089';
            $client_secret ='157aabd14052e19055413bfec4c29f6d';
            $redirect_uri = 'https://ebrahimtaherkhani.ir/instaApiAuth';
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
