This code prints out the duration of each status change in the issue history, and works as a base code that can be extended to perform time logging, populate fields for reporting, etc.

```
{%set previousStatusDate = issue.fields.created %}
{%for history in issue | fieldHistory("status")%}
  {{-"Duration of status " + history | field ("from_string") + " is " + history | field ("date") | date("diff", previousStatusDate, "milliseconds") + " milliseconds"}}
  {%set previousStatusDate = history | field ("date")%}
{%endfor%}
{{"Duration of status " + issue.fields.status.name + " is " + now | date("diff", previousStatusDate, "milliseconds") + " milliseconds"}}
```
