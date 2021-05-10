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
