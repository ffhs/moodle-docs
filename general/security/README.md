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
    return true;
}
```

### Check if the user is logged in

```php
if(isloggedin()){
    return true;
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

