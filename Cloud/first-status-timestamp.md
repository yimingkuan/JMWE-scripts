This script finds the first time an issue reaches a specified status, and returns its corresponding timestamp
```
{{issue | fieldHistory("status") | find({"to_string": "In Progress"}) | field("date")}}
```
