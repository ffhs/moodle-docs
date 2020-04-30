# mod forum

#### Get wiki forum user entries

```php
\cm_info $cm
// [..]

require_once($CFG->dirroot . '/mod/forum/lib.php');
$records = forum_get_discussions($cm, '', false, -1, -1, true, -1, 0, FORUM_POSTS_ALL_USER_GROUPS, 0);
                
```

