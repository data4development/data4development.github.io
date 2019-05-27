---
title: Cluster
order: 2
suborder: 3
---

Metrics from the Google Kubernetes Engine.

* cronjobs-completed-...: checks on log messages about succesfully completed cron jobs (should be a stable "1")
* get-unknown: counts of log messages of the API for GET requests on md5's that are not in the system (if no data is found, this has not occurred)
* CPU utilization: for each of the nodes in the cluster

{% include gke_cronjobs_updates.html %}
{% include gke_cronjobs_process.html %}
{% include gke_get_unknown_svrl_errors.html %}
{% include gke_cpus.html %}
