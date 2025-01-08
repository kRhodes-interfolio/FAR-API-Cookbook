# App Folder
Now lets take a look at the application folder to start teasing apart some of the decisions behind FAR-API

app/

assets/config

consumers

controllers

errors

graphql

helpers

jobs

mailers

models

paginators

presenters

producers

query_objects

serializers

service_objects

validators

views

Again we have good news because most of this is what you would expect to see in a standard scaffolded rails application. Although we have seen them before, lets dig into each one and dicuss how it connects to each of the parts of the service.


#### Assets/Config
This folder has a manifest file that maps our asset pipeline. This directory and its file are, of course, sparse since this is an API only service and not a monolithic app.

#### Consumers 

The consumers folder houses the logic for consuming kafka messages using the Karafka gem. currently, 4 files exist:
- base_consumer.rb which has common handler methods that are used in the platform consumers
- platform_unit_levels_consumer.rb has methods that are specific to consuming messages about UnitLevel entity types
- platform_units_consumer.rb has methods that are specific to consuming Unit entity types
- cdc_consumer.rb is disconnected from the base_consumer class. This is because the cdc consumer connects to a different Kafka server than the rest of FAR-API and uses a separate configuration file.

** FAR-API has a file at the root of the app called karafka.rb and another called cdc_karafka.rb. There needs to be intentional work to unify or rename theses files.

** To boot up each Karafka server you need to export the relevant configuration file. `export KARAFKA_BOOT_FILE=./cdc_karafka.rb && bundle exec karafka s` and `export KARAFKA_BOOT_FILE=./karafka.rb && bundle exec karafka s`