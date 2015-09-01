## create mirror

### Usage

`stack create mirror {path} [arch=string] [name=string] [newest=boolean] [repoconfig=string] [repoid=string] [urlonly=boolean] [version=string]`

### Description

Create a pallet ISO image from the packages found in the
	repository located at 'URL'.

	Mirroring RHEL repositories works with a subscribed Red Hat frontend.
	Direct access via a url, will not work.

	All other public repositories can use a repoid or url.

	If using a url, "newest" and "urlonly" have no effect. The entire
	distribution will be downloaded.

### Arguments

* `{path}`

   The network location of the repository of packages.


### Parameters
* `[arch=string]`

   Architecture of the mirror. (default = the architecture of 
	of the OS running on this machine).
* `[name=string]`

   The base name for the created pallet. If "repoid" is specified, then
	the base name of the pallet will be the repoid, otherwise the base name
	of the pallet will be 'updates'.
* `[newest=boolean]`

   Get only the latest RPMS from the repo. Default is "no"
	and downloads the entire set of RPMS from the distribution.
* `[repoconfig=string]`

   The path to a repo configuration file. Default: None.
* `[repoid=string]`

   The repoid to mirror. Repoid's are found by executing: "yum repolist".
	Default: None.
* `[urlonly=boolean]`

   Print only the list of RPMS in the repo to be downloaded. 
	Useful for checking what will be downloaded.
	Default is "no."
* `[version=string]`

   The version number of the created pallet. (default = the version of 
	Rocks running on this machine).

### Examples

* `stack create mirror http://mirrors.kernel.org/centos/6.5/updates/x86_64/Packages name=updates version=6.5`

   Creates a mirror for CentOS 6.5 based on the packages from mirrors.kernel.org.
	The pallet ISO will be named 'updates-6.5-0.x86_64.disk1.iso'.

* `stack create mirror repoid=rhel-6-server-rpms newest=yes version=6.5`

   Creates a mirror for RHEL 6.5 based on the latest packages from cdn.redhat.com.
	The pallet ISO will be named rhel-6-server-rpms-6.5-0.x86_64.disk1.iso.


