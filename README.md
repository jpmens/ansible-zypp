# zypp

First stab at an Ansible module (`bash`, not Python) for installation/removal of packages on Suse's SLES and openSUSE.

There appears to be some [Python zypper stuff floating around][1], but I have neither the time nor the inclination to use that, particularly not, as it's not installed by default on either platform (chicken/egg).

See also: [Shell scripts as Ansible modules][2]

## Installation

Copy `zypp` to `$ANSIBLE_LIBRARY` on the management host. (There's no need to make it executable.)

	install -m 444 zypp $ANSIBLE_LIBRARY/zypp

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
* Follow (tail -f) a node's `/var/log/zypp/history` to see operation.


  [1]: http://lists.opensuse.org/opensuse-softwaremgmt/2009-05/msg00001.html
  [2]: http://jpmens.net/2012/07/05/shell-scripts-as-ansible-modules/
