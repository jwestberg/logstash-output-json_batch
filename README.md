# Logstash Plugin

This plugin is a heavily butchered and modified version of the standard logstash http output plugin. That plugin is available [here](https://github.com/logstash-plugins/logstash-output-http). 

It has been modified to only support JSON, but also supports batching of messages into JSON lists.

# Usage

Please note that the name of the plugin when used is `json_batch`, since it only supports json in its current form. If further output formats are added in the future, this might change back to http_batch.

    output {
      json_batch {
        headers => ["Authorization", "Basic YWRtaW46cGFzc3dvcmQxMjM="]
        url => "http://your.site/your/json/update/endpoint"
      }
    }
    
Default batch size is 50, with a wait of at most 5 seconds per send. These can be tweaked with the parameters `flush_size` and `idle_flush_time` respectively.

# Installation 

The easiest way to use this plugin is by installing it through rubygems like any other logstash plugin. To get the latest versio installed, you should run the following command: `bin/logstash-plugin install logstash-output-json_batch`

# Building the gem and installing a local version

To build the gem yourself, use `gem build logstash-output-json_batch.gemspec` in the root of this repository. Alternatively, you can download a built version of the gem from the `dist` branch of this repository. 

To install, run the following command, assuming the gem is in the local directory: `$LOGSTASH_HOME/bin/plugin install logstash-output-json_batch-X.Y.Z.gem`

Direct links to the built versions of the gems are available on the [releases page](https://github.com/lucidworks/logstash-output-json_batch/releases)
