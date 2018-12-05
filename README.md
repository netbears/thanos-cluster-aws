# Thanos

This is a tutorial on how to launch and manage a fully working Thanos cluster in AWS.

The notes are also posted on the [NETBEARS](https://netbears.com/blog/monitoring-alerting-prometheus-aws/) company blog. You might want to check the website out for more tutorials like this.

## What is Thanos?

[Thanos](https://github.com/improbable-eng/thanos) is a set of components that can be composed into a highly available metric system with unlimited storage capacity. It can be added seamlessly on top of existing Prometheus deployments and leverages the Prometheus 2.0 storage format to cost-efficiently store historical metric data in any object storage while retaining fast query latencies. Additionally, it provides a global query view across all Prometheus installations and can merge data from Prometheus HA pairs on the fly.

Thanos's main features are:
1. Global querying view across all connected Prometheus servers
2. Deduplication and merging of metrics collected from Prometheus HA pairs
3. Seamless integration with existing Prometheus setups
4. Any object storage as its only, optional dependency
5. Downsampling historical data for massive query speedup
6. Cross-cluster federation
7. Fault-tolerant query routing
8. Simple gRPC "Store API" for unified data access across all metric data
9. Easy integration points for custom metric providers

## Deploy the stack

### Run the CloudFormation template in the AWS Console
* Login to the AWS console and browse to the CloudFormation section
* Select the cloudformation-template.yaml file
* Before clicking "Create", make sure that you scroll down and tick the “I acknowledge that AWS CloudFormation might create IAM resources” checkbox
* ...drink coffee...
* Go to the URL in the output section for the environment that you want to access

### Main resources created

* 1 AutoScaling Group
* 1 Elastic Load Balancer
* 1 DNS record (for ease of access)

### Monitoring

The stack launches [NodeExporter](https://github.com/prometheus/node_exporter/) (Prometheus exporter for hardware and OS metrics exposed by NIX kernels, written in Go with pluggable metric collectors) on each host inside the cluster.

## Final notes
Need help implementing this?

Feel free to contact us using [this form](https://netbears.com/#contact-form).
