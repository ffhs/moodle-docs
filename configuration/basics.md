# Basics

## Get configurations

#### Get the configuration of the current course

{% tabs %}
{% tab title="Call" %}
```php
$courseconfig = get_config('moodlecourse');
```
{% endtab %}

{% tab title="Respose" %}
```text
stdClass Object
(
    [coursedisplay] => 0
    [courseduration] => 31536000
    [courseenddateenabled] => 1
    [enablecompletion] => 1
    [format] => courseformat
    [groupmode] => 0
    [groupmodeforce] => 0
    [hiddensections] => 1
    [lang] => 
    [maxbytes] => 20971520
    [maxsections] => 52
    [newsitems] => 0
    [numsections] => 5
    [showgrades] => 1
    [showreports] => 0
    [visible] => 1
)

```
{% endtab %}
{% endtabs %}

#### Get the configuration of your plugin

{% tabs %}
{% tab title="Call" %}
```php
$mypluginconfig = get_config('block_exam_overview');
```

```php
$sebversionmacos = get_config('block_exam_overview', 'sebversionmacos')
```
{% endtab %}

{% tab title="Response" %}
```text
stdClass Object ( 
    [sebversionmacos] => 2.2.3 
    [sebversionwindows] => 2.2.2 
    [version] => 2019043000 
)
```

```text
2.2.3
```
{% endtab %}
{% endtabs %}

* If the response doesn't fit your needs. Maybe your are more happy with the default course object. `get_course($courseid)` .

{% page-ref page="../api/course/" %}

## Get user preferences

[https://docs.moodle.org/dev/Preference\_API](https://docs.moodle.org/dev/Preference_API)

{% tabs %}
{% tab title="Call" %}
```php
get_user_preferences($name = null, $default = null, $user = null) 
```
{% endtab %}

{% tab title="Response" %}
```text
Array
(
    [admin_bookmarks] => adminnotifications
    [block_enhanced_course_overview-last_tab] => FS19
    [block_myoverview_last_tab] => courses
    [core_message_migrate_data] => 1
    [drawer-open-nav] => true
    [filemanager_recentviewmode] => 1
    [filepicker_recentlicense] => allrightsreserved
    [filepicker_recentrepository] => 3
    [filepicker_recentviewmode] => 2
    [ifirst] => 
    [ilast] => 
    [lesson_view] => collapsed
    [login_failed_count_since_success] => 1
    [quiz_overview_slotmarks] => 1
    [quiz_report_pagesize] => 30
    [topcoll_toggle_15] => x
    [topcoll_toggle_16] => ij
    [topcoll_toggle_17] => v
    [topcoll_toggle_18] => v
    [topcoll_toggle_19] => v
    [userselector_autoselectunique] => 0
    [userselector_preserveselected] => 0
    [userselector_searchanywhere] => 0
    [_lastloaded] => 1556809923
)

```
{% endtab %}

{% tab title="DB" %}
This information is stored in the `mdl_user_preferences` table
{% endtab %}
{% endtabs %}

## Get user settings

```text
@todo
```

