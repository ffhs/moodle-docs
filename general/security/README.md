# Security

### Check if the user is site-admin

```php
if (is_siteadmin($userid)) {
    return true;
}
```

### Check if the user is a guest

```php
if(isguestuser()){
    return null;
}
```

### Check if the user is logged in

```php
if(!isloggedin()){
    return null;
}
```

### Require Login

```php
require_login()
```

* [https://docs.moodle.org/dev/Access\_API\#require\_login.28.29](https://docs.moodle.org/dev/Access_API#require_login.28.29)
* Each plugin script should include require\_login\(\) or require\_course\_login\(\) after setting up PAGE-&gt;url.
* [https://github.com/moodle/moodle/blob/master/lib/accesslib.php\#L838-L844](https://github.com/moodle/moodle/blob/master/lib/accesslib.php#L838-L844) 
* @todo explain better

### Get all roles a user belongs to

{% tabs %}
{% tab title="Call" %}
```php
<?php
// Get the assigned roles.
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

### Check if a user has a capability

```php
<?php
if (has_capability('moodle/course:update', context_system::instance())
```

{% page-ref page="capability.md" %}

### Display a list of users who may be able to access the current activity

```php
$info = new \core_availability\info_module($cm);
$filtered = $info->filter_user_list($users);
```

### Check if the current user can access all settings

```php
<?php
if ($ADMIN->fulltree) {
}
```

More informations about settings can be found here:

{% page-ref page="../../configuration/global-settings/" %}

