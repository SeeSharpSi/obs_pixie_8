---
subject: tech_to_learn
tags:
 - gtri
 - overview
tech:
 - azure
 - aws
 - openshift
type: reference
topic: work
---

# Related Notes
```dataview
LIST
FROM #gtri 
WHERE contains(tech, "azure") or contains(tech, "aws") or contains(tech, "openshift")
```
# Subjects
```dataview
LIST tech FROM #overview AND #gtri
```

# todo
```dataview
TASK
FROM #gtri 
WHERE contains(tech, "azure") or contains(tech, "aws") or contains(tech, "openshift")
```

# Azure

## todo
```dataview
TASK
FROM #gtri 
WHERE contains(tech, "azure")
```

# OpenShift

## todo
```dataview
TASK
FROM #gtri 
WHERE contains(tech, "openshift")
```

# AWS

## todo
```dataview
TASK
FROM #gtri 
WHERE contains(tech, "aws")
```