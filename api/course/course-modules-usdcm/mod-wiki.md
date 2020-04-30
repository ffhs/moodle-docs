# mod wiki

#### Get wiki wiki user entries

```php
\cm_info $cm
// [..]

require_once($CFG->dirroot . '/mod/wiki/locallib.php');
$records = [];
$subwikis = wiki_get_subwikis($cm->instance);
foreach ($subwikis as $subwiki) {
$subwikirecords = wiki_get_page_list($subwiki->id);
                $records = array_merge($records, $subwikirecords);
}
```

