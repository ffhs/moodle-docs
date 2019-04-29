# Capability

### Check if current user has a capability in a specific course

A conveniend function that tests has\_capability, and displays an error if the user does not have that capability.

```php
$coursecontext = context_course::instance($course->id);
try{
    require_capability('moodle/course:manageactivities', $coursecontext)
}catch(\Exception $e){
    // Handle Exception
}
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

### Permission

Permission is a value assigned for capability

## Warnings

{% hint style="warning" %}
Be careful when you remove a capability in `access.php` you have to remove all occourences in your code
{% endhint %}

