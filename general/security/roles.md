---
description: 'Roles assigned to Users (Students, Teachers)'
---

# Roles

## Global Roles

```text
@todo
```

## Roles in a contex

#### Get all roles a user belongs to

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

#### Check if a user has a certain role somewhere in moodle

@todo \(function not tested\)

```php
if (user_has_role_assignment($user->id, $roleid))
    echo "User is a teacher in some course";
```

#### Get the teachers of a course

```php
$teachernames = [];
$context = context_course::instance($courseid);
$role = $DB->get_record('role', array('shortname' => 'editingteacher'));
$roleusers = get_role_users($role->id, );

// Get all teachers' names as an array according the teacher name style setting.
$teachernames = array_map(function($obj) {
    return $obj->firstname . ' ' . $obj->lastname;
}, $roleusers);
```

#### Check if a user has a role in a course

```text
@todo
```

#### Get role with roles function

```php
// The true at the end is used to return an array for select elements.
// So this returns an array with array(roleid => 'originalrolename')
$options = role_fix_names(
     get_all_roles(), 
     context_system::instance(), 
     ROLENAME_ORIGINAL, 
     true
     );
```

#### 

