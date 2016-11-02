#Tyk Plugin Demo Ruby

This plugin will allow users to write middleware for Tyk using [Ruby](https://www.ruby-lang.org).


##Build Requirements

* [Ruby 2.x](https://www.ruby-lang.org)
* [Go](https://golang.org/)
* [gRPC](https://www.grpc.io/) `gem install grpc:1.0.0 grpc-tools:1.0.0`
    * <small>There are currently [issues with the latest and the precompiled versions](https://github.com/grpc/grpc/issues/7727) of the grpc gem so it is advised that you install version "1.0.0" for the time being.</small>


##Usage

To use, first clone and build Tyk locally with the `coprocess` grpc build tag:

    go build -tags 'coprocess grpc'

Next you will need to clone this repo and `cd` into its location on your filesystem. This repo contains the Sample Server which you will need to run with the following command:

    ruby sample_server.rb

In another terminal, run your tyk instance. A simple way to do this would be to navigate into the tyk repository and run the following:

    ./tyk

In a third terminal navigate back to your cloned version of [this repo](https://github.com/TykTechnologies/tyk-plugin-demo-ruby) and run the following cURL request:

    curl -v http://localhost:8080/grpc-api-test/headers

This will then make a request to the server using the middleware defined in the `grpc_app_sample.json` file.
