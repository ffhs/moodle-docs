# Access restrictions

### Access any special acccess restrictions on a activity

{% hint style="warning" %}
Usually this is not nessessary, since you can check all access restrictions by just checking the uservisibility on a **course module**. 

```php
if ($cm->uservisible) {
    return true;
}
```
{% endhint %}

```php
        $availabilities = json_decode($cm->availability);
        if ($availabilities) {
            foreach ($availabilities->c as $availability) {
                if ($availability->type == 'group') {
                    // Find allowed groups in this activity
                    $groups = groups_get_activity_allowed_groups($cm);
                    if (!isset($availability->id)) {
                        // When "Any Group" is selected
                        return false;
                    }
                    if (!in_array($availability->id, array_keys($groups))) {
                        return false;
                    }
                }
            }
        }
```

