# Completion and dates

#### Check if a course is complete

```php
if ($completioninfo == null) {
    $completioninfo = new completion_info($course);
}

// Course was completed.
if ($completioninfo->is_enabled() && $completioninfo->is_course_complete($user->id)) {
    return COURSE_TIMELINE_PAST;
}
```

#### Check if a course is in the future

```php
// Start date not reached.
if (!empty($course->startdate) && (course_classify_start_date($course) > $today)) {
    return COURSE_TIMELINE_FUTURE;
}
```

#### Check if a course is in the past

```php
// End date past.
if (!empty($course->enddate) && (course_classify_end_date($course) < $today)) {
    return COURSE_TIMELINE_PAST;
}
```



