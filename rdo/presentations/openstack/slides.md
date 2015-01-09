# An Introduction to OpenStack

## SCALE 13, 2015

## Rich Bowen - rbowen@redhat.com

---

![openstack](images/openstack.png)

note: A Foundation, and a software project.

---

## OpenStack, the Software

OpenStack software controls large pools of compute, storage, and
networking resources throughout a datacenter, managed through a
dashboard or via the OpenStack API.

---

## OpenStack, the Foundation

![foundation](images/foundation.png)

note: Rackspace and NASA solving similar problems, deciding to pool their
resources. Now, a coalition of over 350 companies working together to 
develop the OpenStack software. 

---

![iaas](images/iaas.png)

note: OpenStack fits into this iaas slot, and provides you a way to
create your own self-service iaas for your "customers".

---

## Pets

![pets](images/pets.jpg) 

* Names like 'fluffy', 'spots', and 'fido'
* When they get sick, you stay up all night recompiling their kernel
* Each one is a unique snowflake

<small>Photo CC julie corsi, Flickr</small>

note: Pets vs Cattle metaphor provides an indication that you might need 
something like this.

---

## Cattle

![cattle](images/cattle.jpg)

* Names like DC01M049.cloud.ibm.com
* When they get sick you shoot it and spin up a new one
* Each one is identical, or based off of a limited number of templates
* Moo

<small>Photo CC mgbjay, Flickr</small>

---

![Pets](images/pet_cow.jpg)

---

## Automation

* "Spin up a new one" generally means that it's done in some automated, reproducable manner
* Automation is a key part of the cloud

note: If not the definition, at least the concept

---

![diagram](images/diagram1.png)

note: Originally, this is what the OpenStack platform looked like

---

![layers](images/openstack_layers.png)

note: It's evolved

---

## Projects

* Bare metal (Ironic)
* Block Storage (Cinder)
* Common Libraries (Oslo)
* Compute (Nova)
* DNS Services (Designate)
* Dashboard (Horizon)
* Data processing service (Sahara)
* Database Service (Trove)
* Deployment (TripleO)
* Documentation (No Clever Name)
* Identity (Keystone)

---

* Image Service (Glance)
* Infrastructure (Infra)
* Key management service (Barbican)
* Message service (Zaqar, formerly Marconi)
* Networking (Neutron)
* Object Storage (Swift)
* Orchestration (Heat)
* Quality Assurance (QA)
* Release cycle management (Thierry)
* Shared File Systems (Manila)
* Telemetry (Ceilometer)

---

    This presentation doesn't cover all of the projects, so I'm most
    assuredly missing something.

---

## Shared services

* Communicate via REST API amongst themselves
* Optional components
* Pluggable (ie, choose your own back-end)

---

## Identity

![Keystone](images/keystone.jpg)

* 'Keystone'
* Various identity backends, including LDAP
* Pluggable

---

## Pluggable

![Pluggable](images/plug.jpg)

* Core design principle
* Many of the projects are light wrappers around your favorite back-end
  service (DNS, File storage, Identity, Database, etc.)

---

## Keystone

* Configure centralized policies across users and systems
* Create users and tenants and define permissions for compute, storage and networking resources using role-based access control (RBAC) features
* Integrate with an existing directory like LDAP, allowing for a single source of identity authentication across the enterprise
* User: Get a list of the services that you can access
* Make API requests or log into the web dashboard to create resources owned by your account

---

## Image Service

* 'Glance'

* Disk and server images.
* Store disk and server images in a variety of back-ends, including OpenStack Object Storage.
* Administrators can create base templates from which their users can start new compute instances
* Users can choose from available images, or create their own from existing servers
* Snapshots can also be stored in the Image Service so that virtual machines can be backed up quickly

---

## Image formats

* Raw
* Machine (kernel/ramdisk outside of image, a.k.a. AMI)
* VHD (Hyper-V)
* VDI (VirtualBox)
* qcow2 (Qemu/KVM)
* VMDK (VMWare)
* OVF (VMWare, others)

---

## Telemetry Service

![Ceilometer](images/ceilometer.jpg)

* 'Ceilometer'
* Aggregates usage and performance data across the services deployed in an OpenStack cloud.
* Reporting (billing)
* Alarming (monitoring and notification)

---

## Orchestration Service

![Heat](images/heat.jpg)

* 'Heat'
* Template-driven engine 
* Describe and automate the deployment of infrastructure.

---

## Database Service

* 'Trove'
* Provision and manage multiple database instances as needed.

---

## Compute

* Nova
* This is where your VM runs

---

## Network

* Neutron
* Manages SDN - Software Defined Networking

---

## Storage (block storage)

* Cinder
* Traditional disk-based service

---

## Storage (object storage)

* Swift
* API to put/get files or objects, without caring where they actually get stored

---

## Horizon

* The "control panel"
* Communicates with services via the API, since they could be anywhere

---

![horizon](images/horizon.png)

---

## Deployment

* Install/Deploy is a nightmare
* Every install is different
* There's no "best" way to do things
* Lots of moving parts

---

## Deployment schemes

* 'All-in-one' - great for testing, impractical in the real world
* Any service can share a machine with others, or run on one, or several machines
* Typical is multiple compute nodes, multiple storage nodes, one "control" note containing Horizon, Neutron, Ceilometer, and so on

---

## Devstack

        git clone https://git.openstack.org/openstack-dev/devstack
        cd devstack
        ./stack.sh

---

![devstack](images/devstack.png)

---

![devstack](images/devstack2.png)

---

![devstack](images/devstack3.png)

---

## RDO

* http://openstack.redhat.com

        sudo yum install -y http://rdo.fedorapeople.org/rdo-release.rpm
        sudo yum install -y openstack-packstack
        packstack --allinone

---

## RDO

* OpenStack packaged for CentOS, RHEL, and Fedora (and derivatives)
* Red Hat engineers working in the upstream
* Community of developers and users sharing their experience

---

## Alternatives

* Crowbar (Dell)
* Fuel (Mirantis)
* Helion (HP)

---

## Why so many?

* This is the place where, for the moment, companies are competing
* Hopefully soon TripleO will be the defacto solution
* Local variants (Debian vs RHEL, for example) will still exist, based
  on TripleO
* We'll start competing on something else, like management
* Speaking of which, http://manageiq.org/

---

# FIN

* Rich Bowen
* RBowen@RedHat.com
* @rbowen
* @RDOCommunity
