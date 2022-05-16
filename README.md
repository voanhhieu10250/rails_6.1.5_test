# README

- These errors happened when I created this project in Windows system. Everything seem to work well when using WSL to create new project. 
- I had problem with the TestMailer (NameError) when trying to deploy on Heroku. I'd tried to fix it but I failed. So I decided to unable skip the Mailer and Testing files.
- We also had problem when trying to create new rails project on Windows (tzinfo-data). So we used flag -B to prevent rails from running 'bundle install' while creating new project.
- After created rails project, we had to deal with another problem about hashing algorithm that comes with Webpack. So I had to install Figaro gem to apply ENV for NODE_OPTIONS. [https://stackoverflow.com/questions/69394632/webpack-build-failing-with-err-ossl-evp-unsupported#:~:text=export-,NODE_OPTIONS%3D%2D%2Dopenssl%2Dlegacy%2Dprovider,-sachaw%27s%20comment%20to](link)
- Don't forget to add production group in Gemfile for postgre DB. I made this mistake when I deploy this app to Heroku first time.

## COMMANDS:

- create:

  - rails \_6.1.5\_ new rails_6_2 -M -B -j esbuild -T

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
