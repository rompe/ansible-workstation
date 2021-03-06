# ansible-workstation
Ansible playbook to update freshly installed Linux workstations for my needs

## Usage

For the default installation:
```
ansible-pull -U https://github.com/rompe/ansible-workstation
```

In addition, for NFS servers:
```
ansible-pull -U https://github.com/rompe/ansible-workstation nfs-server.yml
```

The host name `localhost` is used per default. This only works if /etc/ansible/hosts ist left
empty or features a `localhost` line.

## To be added manually

Some packages can't be installed using ansible.

#### Eclipse
Since the Eclipse packages that come with Fedora tend to break in various ways with every new
release, I am switching to installing Eclipse manually using the
[Eclipse installer](https://www.eclipse.org/downloads/packages/installer)
and selecting the *Eclipse Committers* package.

Just drag & drop the *Install* buttons of these projects onto a running eclipse:

* [PyDev](https://marketplace.eclipse.org/content/pydev-python-ide-eclipse)
* [Mylyn GitLab Connector](https://marketplace.eclipse.org/content/mylyn-gitlab-connector) (If the marketplace client shows this one as incompatible, use "Install new software -> Add" and add http://pweingardt.github.com/mylyn-gitlab as an update site.)
* [LiClipse Text](https://marketplace.eclipse.org/content/liclipsetext)
* [YEdit](https://marketplace.eclipse.org/content/yedit)
* [TM Terminal](https://marketplace.eclipse.org/content/tm-terminal)
* [EasyShell](https://marketplace.eclipse.org/content/easyshell)
* [AnyEdit Tools](https://marketplace.eclipse.org/content/anyedit-tools)
* [MoreUnit](https://marketplace.eclipse.org/content/moreunit)
* [Eclipse Docker Tooling](https://marketplace.eclipse.org/content/eclipse-docker-tooling)
* [Subclipse](https://marketplace.eclipse.org/content/subclipse)

For the EGit Mylyn Connector (which should be
[here](http://marketplace.eclipse.org/content/github-mylyn-connector) but isn't at the moment),
add these Update Sites:

* http://download.eclipse.org/egit/updates
* http://download.eclipse.org/egit/github/updates

Maybe the marketplace page is gone because the project is getting integrated to the main bundle?
Check that.

For the Mylyn Web Templates connector the incubator has to be added to the update sites:

* http://download.eclipse.org/mylyn/incubator/latest/

##### Mylyn GitLab Connector

The connector is outdated since Gitlab dropped API v3 nearly a year ago. 
See here: https://github.com/pweingardt/mylyn-gitlab/issues/47

Since there is no upstream progress, I built
[this updated fork](https://github.com/scriptninja/mylyn-gitlab) 
myself and published the result as an update site:

https://eclipse.rompe.org/mylyn-gitlab

Just add this site to Eclipse and install the connector.

## Disclaimer

If you aren't me, you probably don't want to use this.
