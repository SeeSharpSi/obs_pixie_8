---
title: "bootc: Getting started with bootable containers"
created: 2026-05-20
reason:
source: "https://developers.redhat.com/articles/2024/09/24/bootc-getting-started-bootable-containers"
author:
  - "[[Valentin Rothberg]]"
  - "[[Preethi Thomas]]"
published: 2024-09-24
description: "With bootc (bootable containers), you can use the same container technology for building and managing immutable operating systems. Check out these two video demos and learn how to get started."
tags:
  - "clippings"
type: clipping
topic: tech
---
Bootable containers are a concept that has gained a lot of attention in the open source community, on [Hacker News](https://news.ycombinator.com/item?id=40289120), and especially in the press since [Red Hat Summit 2024](https://developers.redhat.com/articles/2024/05/07/image-mode-rhel-bootable-containers). The [bootc project](https://github.com/containers/bootc) is the core technology that enables OCI containers to encompass complete operating systems, and it is the heart of [image mode for Red Hat Enterprise Linux](https://red.ht/imagemode).

I believe that bootable containers will change how we think about the IT infrastructure of the future. To help users understand and use bootable containers, we have created a [getting started guide](https://docs.fedoraproject.org/en-US/bootc/getting-started/) in the upstream Fedora documentation. This post is meant to introduce you to the basic concepts and help you navigate the rest of the documentation.

![Graphic depicting a container image that includes the kernel](https://developers.redhat.com/sites/default/files/styles/article_floated/public/image1_62.png.webp?itok=c0vYglLs)

Figure 1: Applications containers share the kernel of the underlying OS. Bootable containers include a kernel as they define the underlying OS.

Get started with bootc with video demos

## Get started with bootc with video demos

To make things a bit more interactive, I have recorded a presentation based on the Fedora getting started guide.

![](https://www.youtube.com/watch?v=bf1xqjLeA9M)

I further sat down and recorded a hands-on demo working with bootable containers on my Mac that includes building a bootc image, running it in a VM on my machine and updating it.

![](https://www.youtube.com/watch?v=fccox6sGCWA)

## Get support and share feedback

If you have any questions or feedback, feel more than welcome to join the conversation on [Fedora Discussion](https://discussion.fedoraproject.org/search?q=bootc) and the [bootc community](http://docs.fedoraproject.org/en-US/bootc/community).