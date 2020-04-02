# Capability

### Check if current user has a capability in a specific course

A conveniend function that tests has\_capability, and displays an error if the user does not have that capability.

```php
$coursecontext = context_course::instance($course->id);
require_capability('moodle/course:manageactivities', $coursecontext)
```

### Check if current user has a capability in a specific course category

```php
// $catid must be set, if not it will not check the capability.
if (isset($catid) && 
    !has_capability('moodle/course:upload', context_coursecat::instance($catid))) {
        return false;
}

// Do more stuff here.
```

### Check if a user can access global settings/configuration

```php
has_capability('moodle/site:config', context_system::instance());
```

### Examples of capabilities

* mod/forum:replypost
* moodle/site:config
* moodle/course:upload
* ...

### [Permissions](https://docs.moodle.org/37/en/Permissions)

Permission is a value assigned for capability and can be given to roles in different contexts. Furthermore, it's possible to [override ](https://docs.moodle.org/37/en/Override_permissions)a specific role permissions in a specific context.

To `fetch all permissions` in a specific context you can use this example:

```php
$roles = get_all_roles();
$context = context_module::instance($cm->id);

foreach ($roles as $role) {
    $role = $DB->get_record('role', array('shortname' => $role->shortname));
    $capabilities = get_capabilities_from_role_on_context($role, $context);
}
```

This capabilities can be set on a different course module \(like `inherit`...\):

```php
foreach ($capabilities as $cap) {
    assign_capability($cap->capability, $cap->permission, $cap->roleid, $context->id, true);
}
```

## Warnings

{% hint style="warning" %}
Be careful when you remove a capability in `access.php` you have to remove all occourences in your code.
{% endhint %}

