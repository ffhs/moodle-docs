# Plugins

## Call all plugins with a certain function

{% tabs %}
{% tab title="Call" %}
{% code-tabs %}
{% code-tabs-item title="lib/classes/user.php" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

