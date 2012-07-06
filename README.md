# zypp

First stab at an Ansible module for installation/removal of packages on Suse's SLES and openSUSE.

## Usage

	zypp
		pkg= package-name
		state= installed|removed (default: installed)


Do not, *repeat: NOT*, pass shell-metacharacters in any of the arguments.

## Playbook

	- name: Install editor
	  action: zypp pkg=vim state=installed

## Notes

* zypper on openSUSE 12.1 always exits with 0 -- that's a BUG
* Follow (tail -f) a node's `/var/log/zypp/history' to see operation.
