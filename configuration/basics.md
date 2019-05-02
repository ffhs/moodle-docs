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

### Get user preferences

```php
get_user_preferences($name = null, $default = null, $user = null) 
```



