# Basics

### Get the configuration of the current course

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

* If the response doesn't fit your needs. Maybe your are more happy with the default course object. `get_course($courseid)` .

{% page-ref page="../api/course/" %}

### Get user preferences

```php
get_user_preferences($name = null, $default = null, $user = null) 
```

### Get plugin configurations

{% tabs %}
{% tab title="Call" %}
@todo
{% endtab %}

{% tab title="Response" %}

{% endtab %}
{% endtabs %}



