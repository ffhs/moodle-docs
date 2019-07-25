# Recyclebin

Recycled courses are stored in files: @see 

{% code-tabs %}
{% code-tabs-item title="admin/tool/recyclebin/classes/course\_bin.php" %}
```php
// #214
$files = $fs->get_area_files(
    $context->id, 
    'tool_recyclebin', 
    TOOL_RECYCLEBIN_COURSE_BIN_FILEAREA, 
    $item->id,
    'itemid, filepath, filename', 
    false
);
```
{% endcode-tabs-item %}
{% endcode-tabs %}

The recycled items are linked in the db table `mdl_tool_recyclebin_course`, but the orginal ids are lost

