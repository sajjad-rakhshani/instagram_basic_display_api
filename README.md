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
$curl = curl_init($url);
curl_setopt($curl,CURLOPT_POST,true);
curl_setopt($curl,CURLOPT_POSTFIELDS,$access_token_parameters);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);
$result = curl_exec($curl);
curl_close($curl);
$result = json_decode($result);
$access_token = $result->access_token;
$user_id = $result->user_id;
//get media
$api_url = 'https://graph.instagram.com/me/media?fields=caption,permalink,timestamp,media_url,thumbnail_url&access_token=' . $access_token;
$connection_c = curl_init();
curl_setopt( $connection_c, CURLOPT_URL, $api_url );
curl_setopt( $connection_c, CURLOPT_RETURNTRANSFER, 1 );
curl_setopt( $connection_c, CURLOPT_TIMEOUT, 20 );
$json_return = curl_exec( $connection_c );
curl_close( $connection_c );
$res = json_decode( $json_return );
$posts = $res->data;
```
