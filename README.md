This repository is a very simple Flask application that tries to demonstrate how to use the OpenTelemetry Collector in a Heroku application to send telemetry data to Datadog.

This uses [a fork](https://github.com/arapulido/heroku-buildpack-otelcol) of the [Djiit's Otel Collector buildpack](https://github.com/Djiit/heroku-buildpack-otelcol) that allows to select the contrib distribution of the collector.

To try this application follow the steps below:

```
# Get the code of the application
git clone https://github.com/arapulido/heroku-otel-example/
cd heroku-otel-example

# Create the Heroku application
heroku create heroku-otel-example

# Add the Otel Collector buildpack
heroku buildpacks:add https://github.com/arapulido/heroku-buildpack-otelcol

# Tell the Otel Collector buildpack to use the contrib distribution
heroku config:add OTELCOL_CONTRIB=true
```

Edit the `otelcol/config.yml` file to add your Datadog API key under [`api.key`](https://github.com/arapulido/heroku-otel-example/blob/main/otelcol/config.yml#L53-L59):

![OTEL Configuration](/img/otel_config.png)

Commit and push your changes to Heroku:

```
git add .
git commit -m "Add Datadog API Key"
git push heroku main
```
