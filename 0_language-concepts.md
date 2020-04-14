# WDL Language Concepts

This is a list of WDL language concepts (keywords)  

Top-level keywords
- `version` - WDL Version - currently `1.0`
- `##` - workflow comments
- `import` - import another WDL file and alias with `as`
---
Workflow-level keywords
- `workflow` - list of variables and called tasks
    - `input` - files and/or env config values
    - `if` - check condition for task execution
        - `scatter` - parallelize a task call
            - `call` - run a task in a workflow
                - `input` - files and/or env config values for this task execution
                - `batch_size` - set batch size (for scattered task executions)
    - parameters - in the form of `${param_name}`
    - variables - strongly typed
---
Task-level keywords

- `task` - action, includes...
    - `#` - task or command-level comments
    - `input` - files and/or env config values
    - `command` - runs a script
        - alternate param syntax...
            - `command <<< .... "~{myParam}"... >>>`
    - `output` - produces a result (usually a file)
    - `runtime` - execution environment 
        - `docker` - path to docker image
        - `memory` - allocated memory for runtime
        - `cpu` - allocated cpu for runtime
        - `disks` - type/size of disks
        - `preemtible` - for GCP - use preemtible VMs
        - `continueOnReturnCode` - ususally [0.1]

    - `meta` - metadata for WDL file
        - `author`- author name
        - `email` - author email
        - `version` - version of workflow
        - `last_modified` - date
        - `last_revived_by` - name
    - variables - strongly typed
    - parameters - in the form of `${param_name}`
        - `param_meta` - at task level

  ---  


This is a list of language features

- Refactor via 'imports' - refer to other WDL files
- 1 workflow per WDL file
- Multiple tasks per workflow per WDL file
- Strong typing for variables
- Parameters assigned at scope (workflow, task, command)
- Key-valye input files for params assignments - usually `input.json`
    - `{"WorkflowName.ParamName": "workflowParamValue",`
    - `"WorkflowName.TaskName.ParamName": "taskParamValue",}`
- Comments - designated with `##` (workflow) or `#` (task)