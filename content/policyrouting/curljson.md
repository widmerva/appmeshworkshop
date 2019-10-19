---
title: "Check results"
date: 2018-09-18T17:39:30-05:00
weight: 10
---

* Run the following script to check if you are consistently getting a canary response from crystal. You can compare these results with the random results from the web interface.

```bash
# Define variables #
URL=$(jq < cfn-output.json -r '.ExternalLoadBalancerDNS');
# Execute curl #
for ((i=1;i<=15;i++)); do
      curl --location --silent --header "canary_fleet: true" $URL/json | jq ' .';
done
```