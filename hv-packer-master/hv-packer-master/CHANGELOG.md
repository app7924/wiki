# Changelog

## Version 1.5.0 2021-01-21

* [Ubuntu] added Ubuntu (in experimental mode)
* [Ubuntu] added `Ubuntu 20.04` support
* [BREAKING_CHANGE] Stop support for CentOS 8.x due to premature project termination. Future revisions will remove CentOS 8 completely in favour of it's replacement

## Version 1.4.4 2020-11-17

* [CentOS] added `CentOS 7.9` support
* [CentOS] added `CentOS 7.9 Docker` support
* [CentOS] added `CentOS 7.9 Vagrant` support
* [CentOS] `CentOS 7.8` doesn't update OS by default anymore
* [Windows]  upgrade `puppet-agent` package to version 5.5.22
* [Extra] smaller adjusts in `extra`

## Version 1.4.3 2020-09-25

* [CentOS] bump SystemCenter Agent to 1.0.3.1028
* [CentOS] bump Zabbix repository version to 4.4
* [CentOS] fixes in `provision.sh` script for CentOS7/CentOS8
* [Windows] upgrade `puppet-agent` package to version 5.5.21

## Version 1.4.2 2020-07-04

* [BREAKING CHANGE] added support for packer >= 1.6.0. This also means previous versions of packer are not supported anymore.
* [Windows] added `Windows Server 2004 Std` support
* [CentOS] added `CentOS 8.2` support
* [CentOS] added `CentOS 8.2 Vagrant` support
* [Extra] smaller scripts improvements
* [Extra] bumped `docker`  version to 19.03.05 - Windows
* [Extra] bumped `puppet-agent` version to 5.5.20 - Windows

## Version 1.4.1 2020-05-31

* [Extra] added parameters to `phase3.ps1` script
* [Extra] unified verbosity in phases output

## Version 1.4.0 2020-05-01

* [Extra] added `rkhunter` package to `provision.sh` script
* [CentOS] Added `CentOS 7.8 2003` support
* [CentOS] Disabled updates `-u false` in CentOS 7.7 template
* Updated `README.md`

## Version 1.3.0 2020-04-22

* [Extra] added parameter for zabbix-agent installation (-z false)
* [Extra] according to provision options firewalld rules are not added or not based on install packages decision. This means - if you no longer need zabbix-agent package, firewalld rules for this package won't be created
* [Linux] added variable `boot_command` to be able to parametrize it via variables file
* [CentOS] Added `CentOS 8.1` support
* [CentOS] Added `CentOS 8.1 Vagrant` support
* [CentOS] Thinned CentOS 7 packages, X-Windows System is not installed by default. Default image size decreased from ~6 GB to ~3.5GB

## Version 1.2.2 2020-04-19

* [Extra] added TLS 1.2 fixes for rest of Powershell scripts
* [Extra] fixed problem with SCVMM agent not being installed (hardcoded name)
* [Extra] added tune2fs 1% change for extra drives in `mkfs_device.sh`
* [Extra] decreased priority for epel repository to 90 from 60
* [Windows] Introduce new variable `update_timeout` to increase time between Windows Update cycles. Currently I couldn't find a stable way to check if previous update cycle completed before jumping into new one. Adding pauses causes less interference between phases.
* improved documentation based on questions

## Version 1.2.1 2020-03-09

* [ALL] added checksum calculations to ps1 scripts
* [Extra] added fix for TLS 1.2 being used in ps1 `extra` scripts
* [Linux] upgrades SCVMM agent to version 1.0.3.1026
* minor logic fixed in scripts, making them more verbose

## Version 1.2.0 2020-01-22

* [BREAKING CHANGE] Windows Server 2019 Standard and Datacenter are supported as templates now
* [BREAKING CHANGE] Switched from `cmd` into `powershell`
* [Extra] reworked scripts (try/catch loops)
* [Windows] added vagrant templates for Windows Server 2019 Std and Datacenter
* [Windows] added `Windows Server 1909 Std`

## Version 1.1.0 2019-10-06

* [BREAKING CHANGE] Windows Server machines (semi-annual editions) are supporting templates now
* [BREAKING CHANGE] use `packer` in version not less then 1.4.4
* [Windows] added `Windows Server 1903 Standard`
* [Extra] reworked scripts.
* obsolete files are now in `.archive` folder, will be removed when all files will switch to templates

## Version 1.0.9 2019-09-30

* [BREAKING CHANGE] - CentOS Machines now support templating and previous version creation
  * all CentOS deploys now consists of main template file (./templates) and var_file (./variables). This will allow to have more than 'latest' version of releases when needed.
* [Extra] reworked scripts
* [CentOS] Upgrade Zabbix repository (4.2)
* [CentOS] Provision script now supports flags to install or not specific portion of packages.
* [Windows] Upgrade to dotnetfx chocolatey package (.net 4.8 by default)

## Version 1.0.8 2019-05-25

* switch to packer `1.4` branch - be aware of syntax changes
* [CentOS] added new deploy - 2 disk machine with separated `/var/lib/docker`
* [Extra] changes in scripts
* [CentOS] added `tmux` to installed packages

## Version 1.0.7 2019-04-29

* It's the last version before massive changes in packer >= 1.4 branch
* [Windows] added more variables in Windows templates:
  * `vm_name`
  * `disk_size`
  * `output_directory`
  * `secondary_iso_image`
* [Windows] switching secure boot to `false` as it could be source of problems in some cases
* [Windows] added  `Windows Server 2019 Standard` as `hv_win2019_std_g2`
* [Windows] added  `Windows Server 2019 Datacenter` as `hv_win2019_dc_g2`
* [Windows] reworked `phase-1.ps1` script to recognise Windows version and adjust proper config for it
* [Windows] reworked `phase-1.ps1` removed Spectre/Meltdown mitigations entries
* [Docs]information `How to adjust autounattended.xml when using different image` now added to all Windows Templates.
* [CentOS] added `reboot` after provisioning, which fixes neofetch config not being present during its customisation phase
* [CentOS] added extra templates to make vagrant boxes from created images
* [Extra] changes in scripts
* [Vagrant] experimental support for Vagrant images (CentOS 7.6 added)

## Version 1.0.6 2018-12-11

* [Windows] added `Windows Server 1809` as `hv_win2016_1809_g2.json`
* [Windows] removed `Windows Server 1709` as obsoleted
* [Windows] lock `puppet-agent` on version 5.5.8
* [Windows] set `Disable-WindowsErrorReporting` for Windows based machines
* [CentOS] added CentOS 7.6 as `hv_centos76_g2.json`
* [CentOS] remove port 8140 from firewalld configuration
* [CentOS] change zabbix repository to version 4.x (agents won't work with Zabbix server below 4.x)
* [CentOS] added log cleaning/rotating after build
* [CentOS] upgraded SCVMM agent to version 1.0.3.1022. For older SCVMM older agent (1.0.2) is also available
* [Windows] added `phase5b-docker.ps1` for Windows's based docker. You can choose which version you'll require inside the script. Also, if `$installCompose = $true` is true, docker-compose will also be installed

## Version 1.0.5 2018-10-03

* updated `extra`
* tested with packer 1.3.0/1.3.1/1.3.2-dev
* [CentOS] removed `hv_centos74_g2`
* [Windows] added support for `Windows Server 1803 Edition (Standard)`
* [Windows] workarounded [https://github.com/hashicorp/packer/issues/6733](https://github.com/hashicorp/packer/issues/6733) by using `pause_before` and `restart_check_command`
* [Windows] removed `hv_win2016_g1`

## Version 1.0.4 2018-05-21

* fixed some inconsistency in `extra` scripts when creating registry entries
* [Windows] fixed `boostrap.ps1` for Windows based machines (inproper output for network list)
* [CentOS] fixes in CentOS `'provision.sh` to include proper config for neofetch
* [CentOS] switch to `neofetch`, reworked motd.sh to use neofetch with config (instead of defaults)
* [CentOS] added `screen` as essential package for CentOS
* added `azure-placeholder.sh` for Azure-related CentOS machines
* switched to packer 1.2.3
* added `disk_block_size` with 1 MiB for Linux/CentOS machines

## Version 1.0.3 2018-02-23

* `BREAKING FEATURE` - preparing switching to submodules/subtree for ./scripts and ./files - to share common code with other providers
* tree structure in `./scripts` and `./files`, moved to `./extras`
* [Windows] adding `phase-3.ps1` script to put less generic stuff there. Just uncomment line with `exit` to get rid of it
* [Windows] added support for `Windows Server 1709 Edition (Standard)`
* [Windows] remove some clutter from `bootstrap.ps1`
* [Windows] added `exit 0` for most of the scripts as some external commands were leaving packer with non-zero exit codes
* [CentOS] added `zeroing.sh` script to make compacting more efficient
* [CentOS] reworked bug with UEFI - this time after deploying from image you can run sscript `/usr/local/bin/uefi.sh` which will recheck and readd CentOS UEFI entries. For SCVMM deployments (which separates vhdx from vmcx) use `RunOnce`
* [CentOS] removed clutter from `provision.sh`
* [CentOS] removed screenfetch, replaced with neofetch
* [CentOS] reworked `motd.sh` in `/etc/profile.d` to reflect .Xauthority existence

## Version 1.0.2 2017-12-17

* workaround for PS module `PSWindowsUpdate` in Windows Templates
* added `nmon`, `jq` and `sssd-libwebclient` to CentOS 7.4 template
* added `temp_path` in templates to point creation of VMs to current script's folder
* tested with packer 1.1.3
* added variable `vlan_id`
* added variable `switch_name`
* resized OS images to 70GB (Windows)
* sector-size change in  PS cleaning script (from 64k to 4MB - double the speed)

## Version 1.0.1

* documentation fixes

## Version 1.0.0

* initial release for github

## prerelease versions

* serious bug with UEFI partitioning in CentOS 7.x generation 2 - `Unable to find \EFI\BOOT\grubx64.efi` [https://blogs.msdn.microsoft.com/virtual_pc_guy/2015/02/11/copying-the-vhd-of-a-generation-2-linux-vmand-not-booting-afterwards/](https://blogs.msdn.microsoft.com/virtual_pc_guy/2015/02/11/copying-the-vhd-of-a-generation-2-linux-vmand-not-booting-afterwards/)
* disabled libvirtd in CentOS 7.4 template
* added support for SystemCenter VMM Linux Agent for CentOS Gen 2 machines - it's required in case of per-template deployment
* changed firewalld default configuration
  * default zone set from `public` to `work`
  * default set of rules for zone 'work'
  * assigning interface `eth0` to zone `work`
  * remove excessive logging for
* changed `/etc/profile.d/motd.sh` to adjust missing XAUTHORITY variable
* made files more generic, removed company's related terms
* added adcli and krb5-workstation packages for CentOS 7.x image
* added CentOS 7.4 Gen 2 template `hv_centos74_g2`
* removed `vlan_id` and `switch_name` settings - revert to default ones for repository to be more generic.
* fixed cmd scripts with Windows current catalog syntax.
* added CentOS 7.4 Gen 2 template `hv_centos74_g2`
* removed `vlan_id` and `switch_name` settings - revert to default ones for repository to be more generic.
* fixed cmd scripts with Windows current catalog syntax.
* added `cmd` scripts for Windows deployment
* initial build
