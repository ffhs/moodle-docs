# Data Manipulation API

### Get data directly from the database

```php
$user = $DB->get_record('user', ['id' => '1']);
```

```php
$DB->get_record_select(
    $table, 
    $select, 
    array $params=null, 
    $fields='*', 
    $strictness=IGNORE_MISSING
)
```

### Insert data directly to the database

```php
protected function create_new_attendance_session($attendance) {
    global $DB;
    $session = new stdClass();
    $session->attendanceid = $attendance->id;
    $session->description = '-';
    $DB->insert_record('attendance_sessions', $session);
}
```

### Using transactions

```php
global $DB;
try {
     $transaction = $DB->start_delegated_transaction();
     $DB->insert_record('foo', $object);
     $DB->insert_record('bar', $otherobject);
 
     // Assuming the both inserts work, we get to the following line.
     $transaction->allow_commit();
 
} catch(Exception $e) {
     $transaction->rollback($e);
}
```

