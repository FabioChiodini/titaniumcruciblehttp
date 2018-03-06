# titaniumcruciblehttp
titanium crucible that logs to HTTP


# logstash input and grok configuration

Here's the simplest configuration to filter the logs produced for a geoip localization via ELK:

```
input {
  http { 
    host => "0.0.0.0"
    port => 5000
    }
}

filter {
  grok {
   match => { "message" => "%{IPV4:client_ipk}" }
  }
  geoip {
      source => "client_ipk"
      target => "geoip"
      database => "/usr/share/logstash/GeoLite2-City.mmdb"
    }
}

[redacted]
```
