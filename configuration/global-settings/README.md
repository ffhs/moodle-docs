---
description: >-
  Global Settings can be defined in the settings.php file on the plugins root
  directory.
---

# Global Settings

### Add a checkbox setting

```php
$settings->add(new admin_setting_configcheckbox( 
    $name,
    $visiblename, 
    $description,
    $defaultsetting));
```

### Add a role selection setting

```php
$name = 'block_exam_overview/rolesallowedtoshowallexams';
$title = get_string('rolesallowedtoshowallexams', 'block_exam_overview', null, true);
$description = get_string('rolesallowedtoshowallexams_desc', 'block_exam_overview', null, true);
$default = array('editingteacher');
$settings->add(new admin_setting_pickroles($name, $title, $description, $default));
```

### Moore setting options

> There are many more at `lib/adminlib.php`

### Access Global Settings

#### With `$CFG`

```php
global $CFG;
$allowcssclasses = $CFG->block_html_allowcssclasses;
```

See the page below for more Informations about $CNF

{% page-ref page="globlal-usdcnf.md" %}

#### Access global settings with `get_config()`

```php
// get_config(plugin: 'block_exam_overview', name: 'sebversionwindows')
get_config('block_exam_overview', 'sebversionwindows')
```

### More informations

{% hint style="warning" %}
In a block plugin, the main block class must override the following method, otherwise **moodle will not know** that a settings.php file is present.

```php
/**
 * @return bool
 */
public function has_config() {
    return true;
}
```
{% endhint %}

{% hint style="warning" %}
It is **not possible** to grant access to admin configurations for **other roles** than admin. Moodle checks the following internally:

```php
has_capability('moodle/site:config', context_system::instance());
```

Usually you don't want to give that permission to other global roles
{% endhint %}

### Advanced

#### How the tree is built

Take a look at the following functions: \(No explanation, just for knowing what to google for\)

{% code-tabs %}
{% code-tabs-item title="settings.php" %}
```php
$examoverview_category = new admin_category('block_exam_overview', 'Exam Overview');
$ADMIN->add('blocksettings', $examoverview_category);

$settings = new admin_settingpage(
        'examoverviewsettings',
        'Exam Overview Subsettings',
        'block/exam_overview:capabilityxyz',
        false,
        context_system::instance()
);
$ADMIN->add('block_exam_overview', $settings);

[..]
$settings->add(new admin_setting_pickroles($name, $title, $description, $default));

```
{% endcode-tabs-item %}
{% endcode-tabs %}

