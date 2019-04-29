# Course

### Get a course 

#### Get a course by its id

{% tabs %}
{% tab title="Call" %}
```php
get_course($courseid);
```
{% endtab %}

{% tab title="Response" %}
```text
stdClass Object
(
    [id] => 16
    [category] => 1
    [sortorder] => 0
    [fullname] => Template, Referenzkurs, 2018
    [shortname] => Template Ref 2018
    [idnumber] => 
    [summary] => 
    [summaryformat] => 0
    [format] => courseformat
    [showgrades] => 1
    [newsitems] => 5
    [startdate] => 978303600
    [enddate] => 0
    [marker] => 0
    [maxbytes] => 20971520
    [legacyfiles] => 2
    [showreports] => 1
    [visible] => 1
    [visibleold] => 1
    [groupmode] => 0
    [groupmodeforce] => 0
    [defaultgroupingid] => 0
    [lang] => 
    [calendartype] => 
    [theme] => 
    [timecreated] => 1431090387
    [timemodified] => 1548773995
    [requested] => 0
    [enablecompletion] => 1
    [completionnotify] => 0
    [cacherev] => 1554283959
)
```
{% endtab %}
{% endtabs %}

#### Get a course by the global variable $COURSE

* Attention! Be sure you are in a context where the global variable is initialized.

{% tabs %}
{% tab title="Call" %}
```php
global $COURSE
$currentcourse = $COURSE;
```
{% endtab %}

{% tab title="Response" %}
```php
stdClass Object
(
    [id] => 15
    [category] => 2
    [sortorder] => 20001
    [fullname] => Online-Prüfungen: BWL1-HS18/19
    [shortname] => BWL1.HS18/19
    [idnumber] => 
    [summary] => 
    [summaryformat] => 1
    [format] => courseformat
    [showgrades] => 1
    [newsitems] => 0
    [startdate] => 1550617200
    [enddate] => 1553273520
    [marker] => 0
    [maxbytes] => 20971520
    [legacyfiles] => 0
    [showreports] => 1
    [visible] => 1
    [visibleold] => 1
    [groupmode] => 0
    [groupmodeforce] => 0
    [defaultgroupingid] => 0
    [lang] => 
    [calendartype] => 
    [theme] => 
    [timecreated] => 1550561490
    [timemodified] => 1554224121
    [requested] => 0
    [enablecompletion] => 1
    [completionnotify] => 0
    [cacherev] => 1554295408
)
```
{% endtab %}
{% endtabs %}

#### Get a course by directly accessing the database

* This method allows you to add search parameters

{% tabs %}
{% tab title="Call" %}
```php
$course = $DB->get_record('course', array('shortname' => 'A1'));
```
{% endtab %}

{% tab title="Response" %}
```php

```
{% endtab %}
{% endtabs %}

### Get multiple courses

#### General

{% tabs %}
{% tab title="Call" %}
```php
<?php
// get_courses(categoryid: 'all', sort: 'c.shortname', fields: 'c.id,c.enddate');
get_courses('all', 'c.shortname', 'c.id,c.enddate');
```
{% endtab %}

{% tab title="Response" %}

{% endtab %}

{% tab title="Examples" %}

{% endtab %}

{% tab title="Optional parameters" %}

{% endtab %}
{% endtabs %}

#### Get courses the current user is enrolled

{% tabs %}
{% tab title="Call" %}
```php
<?php
/**
 * @param string|array $fields Extra fields to be returned (array or comma-separated list).
 * @param string|null $sort Comma separated list of fields to sort by, defaults to respecting navsortmycoursessort.
 * @param int $limit max number of courses
 * @param array $courseids the list of course ids to filter by
 * @param bool $allaccessible Include courses user is not enrolled in, but can access
 */
enrol_get_my_courses(['id', 'enddate'], 'startdate DESC,fullname ASC');
```
{% endtab %}

{% tab title="Response" %}

{% endtab %}

{% tab title="Examples" %}

{% endtab %}

{% tab title="Optional parameters" %}
```text

```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="Call" %}
```php
function course_get_enrolled_courses_for_logged_in_user(
    int $limit = 0,
    int $offset = 0,
    string $sort = null,
    string $fields = null,
    int $dbquerylimit = COURSE_DB_QUERY_LIMIT,
    array $includecourses = [],
    array $hiddencourses = []
)
```
{% endtab %}

{% tab title="Response" %}
```php
final class Generator
```
{% endtab %}
{% endtabs %}

### Get all modules in a course

{% tabs %}
{% tab title="Call" %}
```php
$modinfo = get_fast_modinfo($course);
```
{% endtab %}

{% tab title="Response" %}

{% endtab %}

{% tab title="Examples" %}
```php
<?php
const MOD_TYPE_ASSIGN = 'assign';
// [..]

foreach ($modinfo->get_cms() as $cmid => $cm) {
    // Skip activities that are not assignments.
    if ($cm->modname != self::MOD_TYPE_ASSIGN) {
        continue;
    }
    // Skip activities that are not visible.
    // $cm = $modinfo->get_cm($cmid);
    if ($cm->uservisible) {
        // User can access the activity.
    } else if ($cm->availableinfo) {
        // User cannot access the activity, but on the course page they will
        // see a link to it, greyed-out, with information (HTML format) from
        // $cm->availableinfo about why they can't access it.
    } else {
        // User cannot access the activity and they will not see it at all.
    }
}
```

```php
<?php
$modinfo = get_fast_modinfo($course->id, -1);
// $sections = $modinfo->get_sections();
$instances = $modinfo->get_instances_of($modname);
foreach ($instances as $module => $cm) {
    
}
```
{% endtab %}

{% tab title="Optional Parameters" %}
```php
<?php
function get_fast_modinfo($courseorid, $userid = 0, $resetonly = false) {

}
```
{% endtab %}
{% endtabs %}

### Get one specific module of a course with the `course_module_id`

```php
$modinfo = get_fast_modinfo($course);
$cm = $modinfo->get_cm($cmid);
```

## Sections

### Hide a section

```php
set_section_visible($params->courseid, $params->sectionnum, 0);
```

### Loop over course modules and get section informations

```php
/** @var \course_modinfo $modinfo */
$modinfo = get_fast_modinfo($course->id, -1);
    
/** @var cm_info[] $instances */
$instances = $modinfo->get_instances_of($modname);
foreach ($instances as $module => $cm) {
    $section = $modinfo->get_section_info($sectionnum);
    if ($section->visible != 1) {
        continue;
    }
}
```

#### 

{% code-tabs %}
{% code-tabs-item title="lib/modinfolib.php" %}
```php
get_section_info_all()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

