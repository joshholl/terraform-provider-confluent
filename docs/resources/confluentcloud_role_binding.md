---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "confluentcloud_role_binding Resource - terraform-provider-confluentcloud"
subcategory: ""
description: |-
  
---

# confluentcloud_role_binding Resource

`confluentcloud_role_binding` provides a Role Binding resource that enables creating, reading, and deleting role bindings on Confluent Cloud.

## Example Usage

```terraform
resource "confluentcloud_service_account" "test_sa" {
  display_name = "test_sa"
  description = "description for test_sa"
}
resource "confluentcloud_role_binding" "example-rb" {
  principal = "User:${confluentcloud_service_account.test_sa.id}"
  role_name  = "CloudClusterAdmin"
  crn_pattern = confluentcloud_kafka_cluster.standard-cluster-on-aws.rbac_crn  
}
```

<!-- schema generated by tfplugindocs -->
## Argument Reference

The following arguments are supported:

- `principal` - (Required String) A principal User to bind the role to, for example, "User:u-111aaa" for binding to a user "u-111aaa", or "User:sa-111aaa" for binding to a service account "sa-111aaa".
- `role_name` - (Required String) A name of the role to bind to the principal. See [Confluent Cloud RBAC Roles](https://docs.confluent.io/cloud/current/access-management/access-control/cloud-rbac.html#ccloud-rbac-roles) for a full list of supported role names.
- `crn_pattern` - (Required String) A [Confluent Resource Name(CRN)](https://docs.confluent.io/cloud/current/api.html#section/Identifiers-and-URLs/Confluent-Resource-Names-(CRNs)) that specifies the scope and resource patterns necessary for the role to bind.

## Attributes Reference

In addition to the preceding arguments, the following attributes are exported:

- `id` - (String) The ID of the Role Binding (e.g., `rb-f3a90de`).

## Import

You can import a Role Binding by using Role Binding ID, for example:

```
$ terraform import confluentcloud_role_binding.my_rb rb-f3a90de
```