# Unit Test

### Advanced Testcase

#### Resetting the test database and get a data generator \(faker\)

```php
class block_course_checker_attendance_testcase extends \advanced_testcase {
//[..]

    // Reset the database after test (only use it if nessesary)
    $this->resetAfterTest(true);
    
    // Reset all database tables, restore global state 
    // and clear caches and optionally purge dataroot dir.
    $this->resetAllData();
    
    // Get new data generator helper
    $this->generator = $this->getDataGenerator();
```

#### Working with users

```php
// Generate user
/** @var stdClass $teacher */
$teacher = $this->generator->create_user(['email'=>'teacher@moodle.ch']);

// Enrol user in course
$this->generator->enrol_user($teacher->id, $this->course->id, 'teacher', 'manual');

// Switch $USER
$this->setUser($teacher);
$this->setAdminUser();
$this->setGuestUser();

```

### Testing The Data Generator

#### Generate a new instance of an attendance activity

```php
// Create a new course
$newcourse = $this->generator->create_course();

protected function create_new_attendance_activity($course){
    $record['course'] = $course->id;

    /** @var mod_attendance_generator $plugingenerator */
    $plugingenerator = $this->generator->get_plugin_generator('mod_attendance');
    return $plugingenerator->create_instance($record);
}
```



