# README

- These errors happened when I created this project in Windows system. Everything seem to be the same when using WSL to create new project. 
- We also had problem when trying to create new rails project on Windows (tzinfo-data). So we used flag -B to prevent rails from running 'bundle install' while creating new project.
- I had problem with the mail gem when trying to deploy on Heroku. This error is Ruby 3.1-related issues. So I had to add net-smtp, net-imap, net-pop gems to fix it. Read more about this issue [https://stackoverflow.com/questions/70500220/rails-7-ruby-3-1-loaderror-cannot-load-such-file-net-smtp](here)
- After created rails project, we had to deal with another problem about hashing algorithm that comes with Webpack. So I had to install Figaro gem to apply ENV for NODE_OPTIONS. [https://stackoverflow.com/questions/69394632/webpack-build-failing-with-err-ossl-evp-unsupported#:~:text=export-,NODE_OPTIONS%3D%2D%2Dopenssl%2Dlegacy%2Dprovider,-sachaw%27s%20comment%20to](link)
- Don't forget to add production group in Gemfile for postgre DB. I made this mistake when I deploy this app to Heroku first time.

## COMMANDS:

- create:

  - rails \_6.1.5\_ new rails_6_2 -B

- fix tzinfo-data in Gemfile then run:

  - bundle install
  - rails webpacker:install

- fix Webpack hashing algorithm:

  - add figaro gem to the Gemfile and run the following commands:
    - bundle
    - bundle exec figaro install
  - add this ENV to application.yml:
    - NODE_OPTIONS: --openssl-legacy-provider

- run dev env:
  - rails s
