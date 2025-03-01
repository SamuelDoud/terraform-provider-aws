---
subcategory: "WAF Classic"
layout: "aws"
page_title: "AWS: aws_waf_subscribed_rule_group"
description: |-
  Retrieves information about a Managed WAF Rule Group from AWS Marketplace.
---


<!-- Please do not edit this file, it is generated. -->
# Data Source: aws_waf_rule

`aws_waf_subscribed_rule_group` retrieves information about a Managed WAF Rule Group from AWS Marketplace (needs to be subscribed to first).

## Example Usage

```python
# DO NOT EDIT. Code generated by 'cdktf convert' - Please report bugs at https://cdk.tf/bug
from constructs import Construct
from cdktf import Token, TerraformStack
#
# Provider bindings are generated by running `cdktf get`.
# See https://cdk.tf/provider-generation for more details.
#
from imports.aws.data_aws_waf_subscribed_rule_group import DataAwsWafSubscribedRuleGroup
from imports.aws.waf_web_acl import WafWebAcl
class MyConvertedCode(TerraformStack):
    def __init__(self, scope, name, *, defaultAction, metricName, name):
        super().__init__(scope, name)
        by_metric_name = DataAwsWafSubscribedRuleGroup(self, "by_metric_name",
            metric_name="F5BotDetectionSignatures"
        )
        by_name = DataAwsWafSubscribedRuleGroup(self, "by_name",
            name="F5 Bot Detection Signatures For AWS WAF"
        )
        WafWebAcl(self, "acl",
            rules=[WafWebAclRules(
                priority=1,
                rule_id=Token.as_string(by_name.id),
                type="GROUP"
            ), WafWebAclRules(
                priority=2,
                rule_id=Token.as_string(by_metric_name.id),
                type="GROUP"
            )
            ],
            default_action=default_action,
            metric_name=metric_name,
            name=name
        )
```

## Argument Reference

This data source supports the following arguments: (at least one needs to be specified)

* `name` - (Optional) Name of the WAF rule group.
* `metric_name` - (Optional) Name of the WAF rule group.

## Attribute Reference

This data source exports the following attributes in addition to the arguments above:

* `id` - ID of the WAF rule group.

<!-- cache-key: cdktf-0.20.8 input-00a62e9c864ee7ccf92e3ef224d8f2eba8db0a1386389825ac9c6ed11e482193 -->