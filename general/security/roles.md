---
description: 'Roles assigned to Users (Students, Teachers)'
---

# Roles

### Global Roles

### Roles on a contex

### Get all roles a user belongs to

{% tabs %}
{% tab title="Call" %}
```php
<?php
// Get the assigned roles in the given context.
$rolesinsystem = get_user_roles(context_system::instance(), $userid);
```
{% endtab %}

{% tab title="Response" %}
```text
Array
(
    [417] => stdClass Object
        (
            [id] => 417
            [roleid] => 1
            [contextid] => 1
            [userid] => 105
            [timemodified] => 1553791985
            [modifierid] => 2
            [component] => 
            [itemid] => 0
            [sortorder] => 0
            [name] => 
            [shortname] => manager
        )

)
```
{% endtab %}

{% tab title="Examples" %}
```php
// Retrieve the assigned roles for the system context only once and remember for next calls of this function.
static $rolesinsystemids;
if ($rolesinsystemids == null) {
    // Get the assigned roles.
    $rolesinsystem = get_user_roles(context_system::instance(), $userid);

    $rolesinsystemids = [];
    foreach ($rolesinsystem as $role) {
        array_push($rolesinsystemids, $role->roleid);
    }
}
```

[https://github.com/moodleuulm/moodle-local\_boostnavigation/blob/master/locallib.php](https://github.com/moodleuulm/moodle-local_boostnavigation/blob/master/locallib.php)
{% endtab %}
{% endtabs %}

