`Abstract for Infra.next, SCALE edition`

## RDO: Packaging OpenStack for CentOS

OpenStack is "Open source software for creating private and public clouds." As with most Open Source projects, they release source code, and leave it to third parties to provide packages and distributions. Also, since OpenStack is a complicated stack of components, deployment can be tricky, and there's a number of third-party solutions for that, too.

RDO is a community effort to provide OpenStack packages for CentOS (and other RPM-based distros, like Fedora and RHEL), and a deployment tool to make it easier to use. In this talk, Rich Bowen, RDO OpenStack Community Liaison, will talk about that effort, the progress so far, and where you can help out in this effort. Along the way, CentOS board member and developer Jim Perrin will help answer difficult questions about CentOS and some of the details of packaging.


## Notes

Notes from https://plus.google.com/communities/110409030763231732154

* RDO is a community effort to package OpenStack for CentOS/Fedora

* Currently using  Fedora dist-git

    yum install fedpkg
    fedpkg clone _package_name_

* So, for example ...

    $> fedpkg clone --anonymous openstack-nova
    $> cd openstack-nova
    $ git remote -v
    origin	git://pkgs.fedoraproject.org/openstack-nova (fetch)
    origin	git://pkgs.fedoraproject.org/openstack-nova (push)

* https://fedoraproject.org/wiki/Join_the_package_collection_maintainers for info on gaining non-anonymous access

* Packaging for Fedora
  * Fedora versioning is in pace with OpenStack versioning

       Fedora 19 = Grizzly
       Fedora 20 = Havana
       Fedora 21 = Icehouse
       Fedora 22 = Juno
       Fedora 23 = Kilo

* Moving to the CentOS build system

* rdopkg

Wrapper around other tools:

    * rebases to new version
    * Introducing new patchs
    * Modifying .spec file
    * Build packages in copr build system
    * Serves as RDO update/CI front end

However, copr - Cool Other Packages Repository - has some stability issues. So hopefully moving to the CentOS build system will address that.

* EL6

There are a number of people who, for a variety of reasons, want to maintain packages for OpenStack (or at least some portion of OpenStack) on EL6. Some of these are research organizations who have VERY LARGE installations of OpenStack (10k's of nodes) on EL6, and aren't ready to migrate those in a hurry, but want the latest coolness.

There are difficulties - in particular, Juno and later require Python 2.7, and EL6 is on 2.6. This is difficult, but not insurmountable.

However, we want to enable people that want to do this work.

"Those who say it's impossible shouldn't interfere with those who are doing it."


* RDO

rdoproject.org

Packages for CentOS/Fedora, and deployment scripts based on Puppet.

NOT forking OpenStack, just packaging. Significant patches should be going upstream.

* Delorean

Taking upstream and automatically building RPMs from them.

When packages break, the maintainer gets an email.

