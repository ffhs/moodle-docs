# Plugins

## Call all plugins with a certain function

{% tabs %}
{% tab title="Call" %}
{% code title="lib/classes/user.php" %}
```php
// Plugins that may define their preferences.
if ($pluginsfunction = get_plugins_with_function('user_preferences')) {
    foreach ($pluginsfunction as $plugintype => $plugins) {
        foreach ($plugins as $function) {
            if (($pluginpreferences = call_user_func($function)) && is_array($pluginpreferences)) {
                $preferences += $pluginpreferences;
            }
        }
    }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}



{% code title="lib/moodlelib.php" %}
```php
function get_list_of_plugins($directory='mod', $exclude='', $basedir='')
```
{% endcode %}

