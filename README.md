# elastic-agent-standalone-buildpack

A Buildpack to configure the Elastic agent as part of the application build process. It is intended to be used in a [multi-buildpack configuration](https://doc.scalingo.com/platform/deployment/buildpacks/multi).

# Usage Example

## Configure Multiple Buildpacks

The buildpack should be configured using a `.buildpacks` file in combination with the [`multi-buildpack`](https://doc.scalingo.com/platform/deployment/buildpacks/multi).

    $ scalingo --app my-app env-set BUILDPACK_URL=https://github.com/Scalingo/multi-buildpack.git

The example given for command line usage would have the following `.buildpacks` file.

    $ cat .buildpacks
    https://github.com/nicolasSagon/elastic-agent-standalone-buildpack
    https://github.com/Scalingo/nodejs-buildpack.git

## Configure Environment Variables

Set the `LOGGING_LOGSTASH_DESTINATION`, `LOGSTASH_USERNAME`, and `LOGSTASH_PASSWORD` environment variables for your application.

    $ scalingo --app my-app env-set LOGGING_LOGSTASH_DESTINATION="your-logstash-url"
    $ scalingo --app my-app env-set LOGSTASH_USERNAME="your-username"
    $ scalingo --app my-app env-set LOGSTASH_PASSWORD="your-password"