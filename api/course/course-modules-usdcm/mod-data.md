# mod data

#### Get database activity user entries

```php
\cm_info $cm
// [..]

require_once($CFG->dirroot . '/mod/data/locallib.php');
$data = $DB->get_record('data', array('id' => $cm->instance), '*', MUST_EXIST);
$currentgroup = groups_get_activity_group($cm, true);
list($records) = data_search_entries($data, $cm, $cm->context, 'list', $currentgroup);
```



