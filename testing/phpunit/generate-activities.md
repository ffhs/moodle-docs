# Generate Activities

```php
/**
 *
 */
protected function init() {
    // Reset the database after test.
    $this->resetAfterTest(true);
    // Get new data generator helper.
    $this->generator = $this->getDataGenerator();
    // Create a new course.
    $this->course = $this->generator->create_course();
}
```

## Generate moodle attendance activity

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

{% hint style="danger" %}
Will not be visibile by `uservisible` \(please fix\)

```php
$modinfo = get_fast_modinfo($course);
        foreach ($modinfo->cms as $cm) {
                if (!$cm->uservisible) {
```
{% endhint %}

## Generate moodle groupings and groups 

```php
/**
 *
 */
protected function create_a_new_grouping_in_course() {
    $record = [];
    $record['courseid'] = $this->course->id;
    return $this->generator->create_grouping($record);
}
/**
 * @param $grouping
 * @param int $count
 * @return array
 * @throws coding_exception
 */
protected function create_new_groups_in_grouping($grouping, int $count = 1) {
    $record = [];
    $record['courseid'] = $this->course->id;
    $groups = [];
    for ($i = 0; $i < $count; $i++) {
        $group = $this->generator->create_group($record);
        $record['groupingid'] = $grouping->id;
        $record['groupid'] = $group->id;
        $this->generator->create_grouping_group($record);
        $groups[] = $group;
    }
    return $groups;
}
```

## Generate moodle assignment activity

```php
/**
 * @param null $course
 * @param array $record
 * @param array $options
 * @return stdClass
 * @throws coding_exception
 */
protected function create_new_assignment_activity($course = null, $record = [], $options = []) {
    if ($course === null) {
        $record['course'] = $this->course->id;
    } else {
        $record['course'] = $course->id;
    }
    if (!isset($options['visible'])) {
        $options['visible'] = 1;
    }
    /** @var mod_assign_generator $plugingenerator */
    $plugingenerator = $this->generator->get_plugin_generator('mod_assign');
    return $plugingenerator->create_instance($record);
}
```

