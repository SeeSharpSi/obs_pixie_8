---
title: "Getting Started with Bootable Containers"
created: 2026-05-20
reason:
source: "https://docs.fedoraproject.org/en-US/bootc/getting-started/"
author:
published:
description: "Learn more about Fedora Linux, the Fedora Project & the Fedora Community."
tags:
  - "clippings"
type: clipping
topic: tech
---
![](https://www.youtube.com/watch?v=bf1xqjLeA9M)

## What is a Bootable Container?

Over the last decade, [OCI containers](https://specs.opencontainers.org/image-spec/) have become a de facto way to deploy a complete functioning Linux user space as an application. A large set of practices and tooling have evolved around them. Bootable containers are a modern opinionated way of deploying, configuring and managing immutable image based Linux systems using those practices and tooling. You can find a mission statement on [github.com/containers/bootable](https://github.com/containers/bootable).

The [bootc documentation](https://bootc-dev.github.io/bootc//) summarizes bootable containers as "transactional, in-place operating system updates using OCI/Docker container images". In other words, updates to the operating system (OS) are shipped by using container images. That implies that the Linux kernel, the bootloader, drivers, etc. are all part of the container image which renders the container image "bootable".

Just like ordinary application containers, you can build bootable containers by using existing container technologies such as [Containerfiles](https://github.com/containers/common/blob/main/docs/Containerfile.5.md) (i.e., [Dockerfiles](https://docs.docker.com/reference/dockerfile)) and with existing tooling such as [Podman](https://podman.io/), [Docker](https://www.docker.com/) or [buildkit](https://github.com/moby/buildkit). You can further store the images on any container registry such as [Quay.io](https://quay.io/), [Docker Hub](https://hub.docker.com/), [the GitHub Container Registry](https://github.com/features/packages) or any internal container registry.

![bootable container](https://docs.fedoraproject.org/en-US/bootc/_images/bootable-container.png)

Bootable containers are a natural evolution of container technologies. For over a decade, containers have evolved into an industry standard of bundling, shipping, and deploying applications. Bootable containers built on top of these existing technologies and extend containers to include the entire operating system along with the Linux kernel to allow for a comprehensive container-native workflow and user experience.

## Why Bootable Containers?

Before going into any further details, you may wonder about the benefits of bootable containers and why should pay attention to this technology? Let’s go through some of the main benefits.

### A Unified Approach for DevOps

Linux already sits at the core of containers. Bootable containers take Linux’s role a step further, letting you manage the entire OS through container-based tooling and concepts, including [GitOps](https://www.redhat.com/en/topics/devops/what-is-gitops) and continuous integration/continuous delivery (CI/CD). This streamlined approach helps address the challenges of managing Linux at scale, whether you’re pushing patches to different locations or bridging gaps between the operations team and the application development cycle.

### Simplified Security

While there are dozens of security benefits of image-based systems, we want to highlight the fact that the OS is shipped in the form of container images. That means we can make use of the advancements of the past decade in container security such as advanced container security tools to address patching, scanning, validation and signing. We can now apply container security scans on the kernel, drivers, the bootloader and more.

### Speed and Ecosystem Integration

Similar to the security benefits, bootable containers integrate into a vast ecosystem of tools and technologies which have emerged around containers. With bootable containers, we can build, deploy and manage our Linux systems at new scale and speed. A consistent feedback from early adopters of bootable containers is the observation of a simplified toolchain for managing all these tasks in less time.

## Bootc

[Bootc](https://bootc-dev.github.io/bootc//) is at the core and center of bootable containers. It is a CLI tool that ships with a number of systemd services and timers to manage a bootable container. Among other things, bootc is responsible for downloading and queuing updates, and can be used by other higher-level tools to manage the system and inspect the system status. For that reason, bootc is an integral part of each bootable container image. For more details, please refer to the [bootc documentation](https://bootc-dev.github.io/bootc//).

## Filesystem Layout

Bootc systems follow the concept of an immutable operating system. Apart from the following two exceptions, `/etc` and `/var`, all directories are mounted read-only once deployed on a physical or virtual machine. However, during a container build the entire file-system is writable.

The fact that most parts of the file system are mounted read-only is an important attribute of deployed bootable containers and something to consider carefully when preparing workloads and updates. For more information, see the [Filesystem Layout page](https://docs.fedoraproject.org/en-US/bootc/filesystem/) which elaborate in great detail on the exact behavior.

## Base Images

At the moment, there are three distributions shipping bootable containers:

The base images of [Fedora](https://fedoraproject.org/) and [CentOS Stream](https://www.centos.org/centos-stream/) are listed and continuously updated on the [base images page](https://docs.fedoraproject.org/en-US/bootc/base-images/). The RHEL bootc images can be found in the [Red Hat Ecosystem Catalog](https://catalog.redhat.com/software/containers/explore); working with these requires a Red Hat account. You can get a no-cost subscription by [joining the Red Hat Developer program](https://developers.redhat.com/register) in just a few clicks. You further need to login to the [Red Hat Container Registry](https://catalog.redhat.com/) and register your machine with subscription-manager which is well explained in the [release blog post](https://www.redhat.com/en/blog/image-mode-red-hat-enterprise-linux-quick-start-guide). If you are using Podman Desktop, you might install the [Red Hat Account Extension](https://developers.redhat.com/articles/2024/05/07/podman-desktop-red-hat-developer-subscription) which automates most of the process.

## Building bootc Images

As mentioned above, bootable containers can be built with existing tooling such as [Containerfiles](https://github.com/containers/common/blob/main/docs/Containerfile.5.md) and Podman. That means you can use any existing bootc base image and customize it to your needs (e.g., install further packages, copy files from the host, run config scripts, etc.) in a container build as exemplified in the following Containerfile:

```
FROM quay.io/fedora/fedora-bootc:42
RUN dnf install -y [system agents] [dependencies] && dnf clean all
COPY [unpackaged application]
COPY [configuration files]
RUN [config scripts]
```

In case the bootable container will be run in `podman-bootc`, see the [podman-bootc](#_podman_bootc) section for setting up `podman-machine` and building the image.

For more details on building derived bootc images, see the [page in the docs](https://docs.fedoraproject.org/en-US/bootc/building-containers/). Note that bootc is still under development. On rare occasions you might encounter problems you can find in the [upstream issue tracker](https://gitlab.com/fedora/bootc/tracker) (requires a GitLab account).

## Conversion to Disk Images

Updates for bootable containers happen in the form of pulling a new image and (re-)booting into it. But how do we install a fresh bootc system? While bootc supports [installing a bootc container on top of an existing system](https://bootc-dev.github.io/bootc//bootc-install.html#using-bootc-install-to-existing-root), it is more common to convert a bootable container into a so-called disk image, such as ISO, raw or qcow2 to provision a new system.

You can convert a bootable container into a disk image with the [bootc-image-builder](https://github.com/osbuild/bootc-image-builder) which itself needs to be executed inside a container. `bootc-image-builder` is a feature-rich tool that further enables you to inject users, SSH keys, and define a partition layout. For more details, see the [upstream documentation](https://github.com/osbuild/bootc-image-builder?tab=readme-ov-file#-arguments). Podman Desktop also ships with a [bootc extension](https://github.com/containers/podman-desktop-extension-bootc) which allows you to build and convert bootc images in just a few clicks. For more information on the extension, please see the [release blog post](https://developers.redhat.com/articles/2024/05/07/podman-desktop-red-hat-developer-subscription#bootc_extension_for_podman_desktop). Once converted, you can boot a disk image by using libvirt and qemu and other virtualization tools as described in [in the docs](https://docs.fedoraproject.org/en-US/bootc/qemu-and-libvirt/).

If you are using [Podman Desktop](https://podman-desktop.io/), you may install the [Podman Desktop bootc extension](https://github.com/containers/podman-desktop-extension-bootc?tab=readme-ov-file#example-images) to manage bootc images and automatically convert them to disk images.

## Running as a container

You may of course run the container you’ve built as a container, but there are important considerations; more on this in [Running as a container](https://docs.fedoraproject.org/en-US/bootc/provisioning-container/).

## podman-bootc

[podman-bootc](https://github.com/containers/podman-bootc) enables a more bootc-native experience. It is a CLI tool that allows you to easily run a local bootc image in a VM and get shell access to it. Under the hood, podman-bootc uses `bootc install to-disk` to make a disk image from the container image.

podman-bootc requires the `podman-machine` package, which provides a podman machine with a rootful connection. The bootable container has to be built inside the running machine.

|  | The package `podman-machine` is not required on MacOS and the locally built container can be used with `podman-bootc` as it is. |
| --- | --- |

The commands to run the Fedora bootc image via podman-bootc may look as follows:

```
# Initialize a new machine with root being the default user
$ podman machine init --rootful --now
```

or start an already initialized rootful podman machine:

```powershell
$ podman machine start
```

You can list available podman machine connections to get the connection name after starting a podman machine by:

```
$ podman system connection list
Name                         URI                                                          Identity                                                   Default     ReadWrite
podman-machine-default       ssh://core@127.0.0.1:38717/run/user/1000/podman/podman.sock  /home/user/.local//containers/podman/machine/machine  false       true
podman-machine-default-root  ssh://root@127.0.0.1:38717/run/podman/podman.sock            /home/user/.local//containers/podman/machine/machine  true        true
```

Use connection `podman-machine-default-root` as a connection for `podman build` to build the image:

```xml
$ podman -c podman-machine-default-root build -t <repository>/<tag> <Containerfile-dir>
```

The path `<Containerfile-dir>` is a path to the directory with only `Containerfile` and files needed for build, `<repository>/<tag>` defines how the image will be named images list.

In the end run the new machine based on the Fedora base image and specify the desired filesystem:

```elixir
$ podman-bootc run --filesystem=xfs <repository>:<tag>
```

where `<repository>:<tag>` are the values set to the image during build, and they are visible when listing available images, e.g.:

```gradle
$ podman -c podman-machine-default-root images
REPOSITORY                   TAG         IMAGE ID      CREATED         SIZE
quay.io/user/bootc        cups        6abca60ceab2  46 minutes ago  2.05 GB
quay.io/fedora/fedora-bootc  41          7b03571fae24  3 hours ago     1.66 GB
```

podman-bootc is still under development but perfectly capable of supporting your development flow. For installation instructions and further details, please refer to the [bootc upstream docs](https://github.com/containers/podman-bootc) and [section in the Fedora docs](https://docs.fedoraproject.org/en-US/bootc/podman-bootc-cli/). If you are running on a Mac, please run `brew install --head podman-bootc` to build and install the latest version.

## Authentication, Users, Groups

There are no default interactive users other than root in the base image. In the default full base images, OpenSSH is running, but there are no hardcoded credentials (passwords or SSH keys). That means that you cannot log into a booted VM without further work (e.g., injecting SSH keys for the root users). For that reason, podman-bootc automatically injects SSH keys such that you can easily get access to the VM. See the [section on authentication](https://docs.fedoraproject.org/en-US/bootc/authentication/) in the docs for more information on this topic.

## Installing on Bare Metal

At this point, you know how to build a bootable container image and how to convert it into a disk image that you may want to install on your machine. Before installing Fedora/CentOS bootc, it’s recommended that you have created a customized derived container image, but this is not a hard requirement, as it is possible to enable basic system access via e.g. injecting SSH keys with kickstart or with [bootc-install](https://bootc-dev.github.io/bootc//bootc-install.html) and the `--root-ssh-authorized-keys` flag. You can find a list of examples and detailed instructions [here](https://docs.fedoraproject.org/en-US/bootc/bare-metal/). You can further find documentation on how to provision public cloud instances on [AWS](https://docs.fedoraproject.org/en-US/bootc/provisioning-aws/) or [GCP](https://docs.fedoraproject.org/en-US/bootc/provisioning-gcp/) and how to install on [vSphere](https://docs.fedoraproject.org/en-US/bootc/provisioning-vsphere/).

## Updating Bootable Containers

|  | Local package layering is not yet available for bootc. Track the issue [here](https://gitlab.com/fedora/bootc/tracker/-/issues/4). |
| --- | --- |

The figure below depicts the life cycle of a bootable container and the different steps required from building to deploying to updating bootc systems. Once a bootable container image has been built, you may convert it to a disk image. The disk image can then be used to install the content in the target environment (e.g., a public cloud instance). You might also want to push the container image to your target container registry.

![updates](https://docs.fedoraproject.org/en-US/bootc/_images/updates.png)

To update existing systems, the process can be repeated: that is building a new image and pushing it to the registry. Once pushed, bootc on the deployed systems can pull down the new image from the registry and reboot into the new image.

There are several ways how an individual system can be updated:

- By default, bootc systems perform **time-based updates** via a systemd timer.
- For **event-based updates**, the `bootc-fetch-apply-updates.service` can be triggered.
- **Manual updates** can be performed by running `bootc-upgrade` and rebooting the system.

An example CI/CD pipeline for a bootc image is outlined in this article, [How to create CI/CD pipelines for image mode for RHEL](https://developers.redhat.com/articles/2024/11/22/creating-cicd-pipelines-image-mode-rhel#).

Bootc further supports rollbacks via the bootc-rollback command. For more details, please refer to the [auto-updates section](https://docs.fedoraproject.org/en-US/bootc/auto-updates/) which further elaborates on disconnected and bootloader updates.

The following hands-on demo shows the update process of a local VM:

![](https://www.youtube.com/watch?v=fccox6sGCWA)

## Next Steps

At that point, we have learned the nature of and the concepts behind bootable containers. From building on top of available bootc base images to testing them locally with podman-bootc to understanding how to update already deployed systems.

The suggested next steps are to try out the technology and browse through the other pages of this documentation.

Want to help? [Learn how to contribute to Fedora Docs ›](https://docs.fedoraproject.org/en-US/fedora-docs/contributing-docs/)