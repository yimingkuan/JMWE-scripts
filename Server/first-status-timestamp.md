This script finds the first time an issue reaches a specified status, and returns its corresponding timestamp

```
import com.atlassian.jira.issue.history.ChangeItemBean

String statusName = "Done"

if(issue.getFieldHistory("status").size > 0) {
  ChangeItemBean statusHistory = issue.getFieldHistory("status").find { it.toString == statusName }
  if(statusHistory != null) {
    return statusHistory.created
  }
}
if(issue.get("status")?.name == statusName) {
  return issue.get("Created")
} else {
  return null
}
```
