---
description: >-
  In the edit_form.php, you can specify settings for the current block-instance.
  For example you can define the title of the block.
---

# Edit Form

### Create new Edit Form

* The key of an form element must contain a `config_` prefix! Otherwise the value will not be saved.

{% code-tabs %}
{% code-tabs-item title="blocks/course\_list/edit\_form.php" %}
```php
class block_course_list_edit_form extends block_edit_form {
    protected function specific_definition($mform) {
        $mform->addElement('header', 'configheader', get_string('blocksettings', 'block'));

        $mform->addElement('text', 'config_title', get_string('configtitle', 'block_course_list'));
        $mform->setType('config_title', PARAM_TEXT);

        $mform->addElement('checkbox', 'config_enablesearchfield', get_string('configenablesearchfield', 'block_course_list'));
        $mform->setType('config_enablesearchfield', PARAM_INT);
    }
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Access the configured data \(in the block\)

{% code-tabs %}
{% code-tabs-item title="blocks/course\_list/block\_course\_list.php" %}
```php
// Get the block title from config
if (!empty($this->config->title)) {
    $this->title = $this->config->title;
}else{
    $this->title = get_string('mycourses');
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### More Informations

* [ https://docs.moodle.org/dev/lib/formslib.php\_Form\_Definition\#advcheckbox](%20https://docs.moodle.org/dev/lib/formslib.php_Form_Definition#advcheckbox)
