# Capability

### Check if current user has a capability in a specific course

A convenience function that tests has\_capability, and displays an error if the user does not have that capability.

```php
$coursecontext = context_course::instance($course->id);
try{
    require_capability('moodle/course:manageactivities', $coursecontext)
}catch(\Exception $e){
    // Handle Exception
}
```

### Examples of capabilities

* mod/forum:replypost

### Check if current user has a capability in a specific course category

```php
// $catid must be set, if not it will not check the capability.
if (isset($catid) && 
    !has_capability('moodle/course:upload', context_coursecat::instance($catid))) {
        return false;
}

// Do more stuff here.
```

### Permission

Permission is a value assigned for capability

