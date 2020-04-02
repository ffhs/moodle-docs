---
description: >-
  Moodle 2.3 and later fully supports PHPUnit tests as part of the code. These
  are automated tests of very low-level code functionality that a developer
  should write as part of any new code.
---

# PHPUnit

## Introduction

More information ca be found here 

[https://docs.moodle.org/dev/Writing\_PHPUnit\_tests](https://docs.moodle.org/dev/Writing_PHPUnit_tests)

## Run unit tests

### Run in the console

{% hint style="warning" %}
Run all unit-tests... if it works, it works  
{% endhint %}

```php
vendor/bin/phpunit
```

#### Run a single test

```php
vendor/bin/phpunit blocks/course_checker/tests/checker_attendance_test.php
```

### Run in PhpStorm

```text
@todo
```

### Reset the database

```text
php /var/www/html/moodle/admin/tool/phpunit/cli/init.php
```

## Advanced Testcase

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

#### Generate, enrol and assign user

```php
// Generate user
/** @var stdClass $teacher */
$teacher = $this->generator->create_user(['email'=>'teacher@moodle.ch']);

// Enrol user in course
$this->generator->enrol_user($teacher->id, $this->course->id, 'teacher', 'manual');

/**
* Assign a role to the current user
* 1 Manager / Admin user
* 4 Teacher
* 5 Student
*
* @see mld_role table
*/
$this->generator->role_assign($roleid, $user->id, false);
```

#### Switch user

```php
$this->setUser($teacher);
$this->setAdminUser();
$this->setGuestUser();
```

## Fake Data

#### Faking random simple data

{% tabs %}
{% tab title="Call" %}
```php
$word = self::word();
```

{% hint style="info" %}
Hint: This is not part of moodle core
{% endhint %}
{% endtab %}

{% tab title="Implementation" %}
```php
/**
 * Returns a random word
 *
 * @param int $len
 * @return bool|string
 */
protected static function word($len = 10) {
    $word = array_merge(range('a', 'z'), range('A', 'Z'));
    shuffle($word);
    return substr(implode($word), 0, $len);
}
```
{% endtab %}
{% endtabs %}

#### Faking with faker class

> Not yet implemented, but use this format if you implement it

Have a look at https://github.com/fzaninotto/Faker

{% tabs %}
{% tab title="Call" %}
```php
$faker->name;
$faker->address;
$faker->text;
$faker->numberBetween(10,20);
..
```
{% endtab %}

{% tab title="Result" %}

{% endtab %}
{% endtabs %}

### Testing the data generator

#### Generate a new instance of an activity

{% page-ref page="generate-activities.md" %}

#### Generate a new block instance

```php
$block = $this->generator->create_block('quote');
```

#### Assign the required capabilities to the block

@todo this need improvement an testing

use: `class block_quote_external_testcase extends \externallib_advanced_testcase`

```php
$contextid = \context_block::instance($block->id)->id;
/** @todo this is not working on the current user */
$roleid = $this->assignUserCapability('moodle/block/quote:add', $contextid);
$this->unassignUserCapability('enrol/manual:enrol', $context1->id, $roleid);
```

## Asserting

### Test if two arrays share the same content

```php
$this->assertEquals($expected, $actual, true);
```

### Test if two array have the same content AND the elements are in the same order

$t~~his-&gt;assertEquals\($expected, $actual, true\);~~

```php
$this->assertEquals(json_encode($expected), json_encode($actual));
```

