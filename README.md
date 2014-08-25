Gollum app with Omniauth using Ruby 1.9.3-p327 .

1. Initial steps to setup the app
a. gem build omnigollum.gemspec
b. gem install omnigollum*.gem
i. Please note, if you face issues installing nokogiri, you need to first try - 'gem install nokogiri -- --use-system-libraries'
c. Basically to add individual authentication strategies one has to add that specific gem in the Gemfile and one has to require the same from the config.rb file. For instance, one can see the same being done for the gem 'omniauth-google-oauth2'.

2. Steps to configure the login -

a. Create a bare git repository with the command - git init --bare name_of_the_wiki.git
b. cp config.rb.example config.rb
c. Add the following to config.rb
i. require 'omniauth-google-oauth2' for google auth if not already present.
ii. authorized_users = ["emaild_id_1", "emaild_id_2", "emaild_id_3", "emaild_id_4"]
c. Add gollum wiki path(for the above created wiki) to your config.rb. You can use pwd cmd for the same to get the exact location where the wiki is created from step d. To get the client id from google, you need to do the following
i. Login to  'https://console.developers.google.com'
ii. Create new project.
iii. Click 'APIs & auth'
iv. Make sure "Contacts API" and "Google+ API" are on.
v. Go to Consent Screen, and provide a 'PRODUCT NAME'
vi. Get the client id and secret by clicking on the Credentials option. Enter the same in config.rb
vii. Enter a redirect_uri to be http://localhost:4567/__omnigollum__/auth/google_oauth2/callback. Without this on successful entry of your credentials you wou'dnot ge
Wait 10 minutes for changes to take effect.


3. A user who is not in the set of authorized_users array(in config.rb) will be able to access the application using the below steps
A user has to hit http://localhost:4567/__omnigollum__/pages in the browser URL.

4. To logout of the application
i. A user has to hit http://localhost:457/__omnigollum__/logout in the browser URL.
ii. 

