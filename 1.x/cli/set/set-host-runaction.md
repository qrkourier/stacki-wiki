## set host runaction

### Usage

`stack set host runaction {host}... {action} [action=string]`

### Description

Set the run action for a list of hosts.

### Arguments

* `{host}`

   One or more host names.

* `{action}`

   The run action to assign to each host. To get a list of all actions,
	execute: "rocks list bootaction".


### Parameters
* `[action=string]`

   Can be used in place of the action argument.

### Examples

* `stack set host runaction compute-0-0 os`

   Sets the run action to "os" for compute-0-0.

* `stack set host runaction compute-0-0 compute-0-1 memtest`

   Sets the run action to "memtest" for compute-0-0 and compute-0-1.

* `stack set host runaction compute-0-0 compute-0-1 action=memtest`

   Same as above.


