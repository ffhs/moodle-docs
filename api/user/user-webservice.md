# User Webservice

#### Update many users in moodle <a id="update_many_users_in_moodle"></a>

```javascript
{
    "body": {
        "wstoken": "<token>",
        "wsfunction": "core_user_update_users",
        "moodlewsrestformat": "json",
		"users": [
			{
				"id": 10264,
				"idnumber": "4BFDFAD606CA409794B99C0693B932EB"
			}
		]
    },
    "debug": false
}
```

**Get one user from moodle**

```javascript
{
    "body": {
        "wstoken": "<token>",
        "wsfunction": "core_user_get_users_by_field",
        "moodlewsrestformat": "json",
        "field": "idnumber",
        "values": [
            "4BFDFAD606CA409794B99C0693B932EB"
        ]
    },
    "debug": false
}
```

