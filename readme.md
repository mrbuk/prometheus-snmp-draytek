# prometheus-snmp-draytek

SNMP configuration for [Prometheus SNMP Exporter](https://github.com/prometheus/snmp_exporter) to collect [Draytek SNMP metrics](https://www.draytek.com/support/knowledge-base/5517)

Use the `snmp.yml` file or generate it yourself using:

```
go install github.com/prometheus/snmp_exporter/generator@latest
export MIBDIRS=$PWD/mibs:$HOME/.snmp/mibs:/usr/local/share/snmp/mibs:/usr/share/snmp/mibs 
$GOPATH/bin/generator generate
```

and run the exporter

```
go install github.com/prometheus/snmp_exporter
~/go/bin/snmp_exporter --config.file ./snmp.yml
```

Check if `http://localhost:9116/snmp?target=192.168.1.1&module=draytek` fetches the metrics as expected (`192.168.1.1` is the IP of the Draytek device)

You might want to merge the generated `snmp.yml` with the one provided by the project.
