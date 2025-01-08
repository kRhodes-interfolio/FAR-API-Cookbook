# Setup
FAR-API is a Rails 6 application running on Ruby 2.7.8.
It serves in a larger web application as a an API-only Ruby on Rails application that uses graphql:Pro to
provide data services.
some of the tools in the FAR-API stack are:
Graphql
Postgres
Redis
Karafka
Factory-bot
Rubocop
AWS for Prod and QA servers
Judging by the stack, a seasoned Rails developer should be relatively comfortable with what is coming
in the cookbook. This paper will serve as an overview to a coming deep dive into the current state of far-
api along with the decisions made and things to come.
Setting up FAR-API for Testing and Console
Setting up FAR for testing is reminicient of standard Rails apps ess