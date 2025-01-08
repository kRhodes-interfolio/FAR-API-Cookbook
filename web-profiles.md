# Web Profiles
Web Profiles is a actually the name of an application of which FAR-API is a critical part. The basic effort
taht far-api contibutes to WP is as a layer that ingests Kafka messages that relate to a change data
capture process, looks up and formats data records based on the Kafka payload, and sends that data to
an external service called Mimir to be displayed in a separate app that would more properly be called
Web Profiles.
To do this, far-api makes use of Karafka as a package to facilitate connections to a Kafka broker,
active_model_serializers to reformat data for use in Mimir and other downstream systems, db_switcher
to select between CDC tenants and an in-house written Mimir gem to make sure that api tokens and
other communication details are mixed in with the code that stictly does what FAR means to do.
Essentially: FAR consumer ingest Kafka messages => the finder module tracks down the record that
has been changed=> the serializer modules transform the retrieved record, a job is created to send the
transform record in a formatted payload to Mimir in the backgound.