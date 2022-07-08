---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "gitea_team Resource - terraform-provider-gitea"
subcategory: ""
description: |-
  gitea_team manages Team that are part of an organisation.
---

# gitea_team (Resource)

`gitea_team` manages Team that are part of an organisation.

## Example Usage

```terraform
resource "gitea_org" "test_org" {
  name = "test-org"
}

resource "gitea_user" "test" {
  username             = "test"
  login_name           = "test"
  password             = "Geheim1!"
  email                = "test@user.dev"
  must_change_password = false
  admin                = true
}


resource "gitea_team" "test_team" {
  name         = "Devs"
  organisation = gitea_org.test_org.name
  description  = "Devs of Test Org"
  permission   = "write"
  members      = [gitea_user.test.username]
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String) Name of the Team
- `organisation` (String) The organisation which this Team is part of.

### Optional

- `can_create_repos` (Boolean) Flag if the Teams members should be able to create Rpositories in the Organisation
- `description` (String) Description of the Team
- `include_all_repositories` (Boolean) Flag if the Teams members should have access to all Repositories in the Organisation
- `members` (List of String) List of Users that should be part of this team
- `permission` (String) Permissions associated with this Team
Can be `none`, `read`, `write`, `admin` or `owner`
- `units` (String) List of types of Repositories that should be allowed to be created from Team members.
Can be `repo.code`, `repo.issues`, `repo.ext_issues`, `repo.wiki`, `repo.pulls`, `repo.releases`, `repo.projects` and/or `repo.ext_wiki`

### Read-Only

- `id` (String) The ID of this resource.

