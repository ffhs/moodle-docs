# mod glossary

#### Get glossary activity user entries

```php
\cm_info $cm
// [..]

require_once($CFG->dirroot . '/mod/glossary/lib.php');
$glossary = $DB->get_record('data', array('id' => $cm->instance), '*', MUST_EXIST);
$options = ['includenotapproved' => true];
list($records) = glossary_get_entries_by_search($glossary, $cm->context, '', 1, 'CONCEPT', 'ASC', 0,
                        999, $options);
```

