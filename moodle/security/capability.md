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

### Permission

Permission is a value assigned for capability

