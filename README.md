[![Build Status](https://api.shippable.com/projects/54d275965ab6cc13528ad353/badge?branchName=master)](https://app.shippable.com/projects/54d275965ab6cc13528ad353/builds/latest)

# Project Calico

Calico represents a new approach to virtual networking, based on the same
scalable IP networking principles as the Internet.

First established in enterprise data centers, virtual networking provides the
logical fabric that enables workloads in virtual machines to communicate
securely, ultimately over a shared physical fabric. Initially this was achieved
by using VLANs; as that approach quickly hit well-known scalability limits,
other techniques such as VXLAN, GRE-based tunnels and SDN controlled flows were
taken. All of these approaches introduced greater complexity and ultimately hit
scalability and performance limits inherent in extending an enterprise-class
layer 2 network over large numbers of servers and wide area links.

A new approach is required. One that recognizes that the vast majority of
today’s workloads are based on IP, and that leverages everything we already
know about how to build high-performance, large-scale networks.

Enter Project Calico. With Calico, we went back to the drawing board and
redesigned how virtual networks should be built, based on an intimate
understanding of the requirements of modern workloads and virtualization
environments.

## What does Calico do?

Calico integrates seamlessly with the cloud orchestration system (such as
OpenStack) to enable secure IP communication between virtual machines. As VMs
are created or destroyed, their IP addresses are advertised to the rest of the
network and they are able to send/receive data over IP just as they would with
the native networking implementation – but with higher security,
[scalability and performance](http://www.projectcalico.org/technical/scalability-and-performance/).

## How do I get started with Project Calico?

To get started, you first need a working installation of
[OpenStack](http://www.openstack.org/). Then download and install the latest
stable build of Calico following the instructions
[here](http://www.projectcalico.org/download/).

Technical documentation is
[here](https://github.com/Metaswitch/calico-docs/wiki);
if you are going to contribute to the project, you'll also need to run the
[tests](doc/CalicoUTs.md).

## How can I get support for Project Calico?

There are two options for getting support for Calico. You can simply
[ask the community](http://www.projectcalico.org/community/) any question you
like – there is an active group of users and developers who will usually try
their best to help you or point you in the right direction. Or you can work
with one of the commercial vendors and system integrators who provide
installation, integration, customization and support services for Calico.

Currently, we are aware of the following vendors who provide commercial support
services:

- Metaswitch Networks.

Please [contact us](http://www.projectcalico.org/contact-us/) if you are a
vendor providing commercial support services and wish to be added to this list.

## Who is behind Project Calico?

Project Calico was founded by Metaswitch Networks, who also contributed the
original implementation to open source and are responsible for the ongoing
management of the project. However, it is open to any members of the community
– individuals or organizations – to get involved and contribute code.

Please [contact us](http://www.projectcalico.org/contact-us/) if you are
interested in getting involved and contributing to the project.

## How do I hack on Calico?

It's great that you're interested! In additional to being able to install
Calico from packages, you can install the source directly. If you want to work
on the code, we recommend installing the source directly in a Python
[virtual environment](http://docs.python-guide.org/en/latest/dev/virtualenvs/).
In your virtual environment, switch to the directory containing the code and
type:

    pip install -e .

This will install the code and all its dependencies, *except for Neutron*. This
is all you need to work on Felix or the ACL Manager. If you want to work on our
OpenStack plugin, you'll also need to install Neutron: doing that is outside
the scope of this article.

### Fewer dependencies

If you only want to hack on one or two components you may not want to install
the dependencies for the others. To do that, you can set the `$CALICODEPS`
environment variable before installing the code. Set the variable to a
comma-separated list of the names of the components you want to install the
dependencies for.

For example, if you want to work on Felix and the ACL manager, you will want to
set it to `felix,acl_manager`. With that set, you can then run
`pip install -e .`, which will install the subset of the dependencies needed
for those components.
