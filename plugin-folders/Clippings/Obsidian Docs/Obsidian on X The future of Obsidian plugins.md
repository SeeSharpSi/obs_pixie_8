---
title: 'Obsidian on X: "The future of Obsidian plugins"'
source: https://x.com/i/status/2054234821875146898
author:
- '[[x.com]]'
published: 2026-05-11
created: 2026-05-12
description: null
---
![Image](https://pbs.twimg.com/media/HIIPQ5gbYAAOQeI?format=png&name=large)

Today we’re excited to launch [Obsidian Community](https://community.obsidian.md/), the new directory and developer dashboard for Obsidian plugins and themes.

Since the [Obsidian API](https://docs.obsidian.md/) release in 2020, more than 4,000 plugins and themes have been created by our amazing community. Incredibly, Obsidian plugins have passed 120 million total downloads!

Our goal is to make it easy and safe for anyone to build, distribute, discover, and use plugins and themes.

Today’s launch is only the start of a larger set of initiatives. We’re excited to share what’s new, and what’s coming soon.

1. Community site
2. Developer dashboard
3. Automated reviews
4. Plugin safety
5. Tools for teams
6. Next steps
7. FAQ

## Community site

The new [Community site](https://community.obsidian.md/) makes it easy to explore the breadth of plugins and themes with new ways to browse, search, filter, and sort.

You can browse plugins across dozens of categories such as [Integrations](https://community.obsidian.md/search?type=plugin&categories=integrations), [Bases](https://community.obsidian.md/search?type=plugin&categories=bases), [Charts](https://community.obsidian.md/search?type=plugin&categories=charts), and [many more categories](https://community.obsidian.md/categories). Sort projects by name, downloads, popularity, release date, and updated date.

Every project has its own detail page where you can find screenshots, details, and a safety scorecard. New labels are present for paid plugins and [official](https://community.obsidian.md/search?type=plugin&official=1) integrations.

Authors can customize their profile pages with sponsorship options and links to their website and social media.

## Developer dashboard

The Obsidian Community site also hosts our new developer dashboard. This is where authors can submit, manage, and track the status of their projects.

All existing plugins, themes, and queued submissions added via [GitHub](https://github.com/obsidianmd/obsidian-releases) have been automatically migrated to the new site.

To claim your existing projects, [sign into](http://127.0.0.1:2999/blog/future-of-plugins/[https://community.obsidian.md/account/]\(https://community.obsidian.md/account/profile\)) the new Community site and connect your GitHub account. This lets you manage your existing projects, submit new projects, and edit your profile page.

## Automated reviews

With this transition we are introducing automated reviews for all community projects. The new automated review system scans **every version** for security and code quality, **not just the initial submission**.

Until today, initial submissions were manually reviewed and approved by our small team to ensure they follow the [Developer Policies](https://docs.obsidian.md/Developer+policies). However, as Obsidian has grown in popularity we struggled to keep pace with submissions, and subsequent versions were not reviewed.

As coding agents accelerate the creation of plugins, the review queue was only getting longer. We don’t expect the pace of new submissions to slow down. With tools like [Obsidian CLI](http://127.0.0.1:2999/cli) we’re making it even easier to create plugins.

Now when a plugin or theme is submitted, the automated review system verifies that it adheres to our developer policies, that the source code follows best practices, and that it is free of known vulnerabilities.

Building on this new system allows us to scalably review community projects going forward. With the ability to continuously improve our automated tests, we are more equipped to comprehensively improve the quality and safety of the Obsidian ecosystem.

Importantly, **manual reviews will continue**. The new system allows us to shift our efforts towards plugins that require deeper inspection such as popular plugins, featured plugins, and issues flagged by the community.

All existing plugins and themes have been re-reviewed using the new system. In this process we found older plugins and themes that do not meet the latest guidelines. These older projects have been temporarily granted an exception. However, all plugins and themes that do not pass the new review process will eventually be phased out of the official directory. See FAQs below.

And… Yes! All queued submissions have been reviewed. With the new system we were able to process over 2,300 queued submissions in the last few days. If you’ve been waiting on us to review your plugin, [sign into](https://community.obsidian.md/account/profile) the Community site to see your submission’s current status.

## Plugin safety

The new Community site and automated review system introduces major enhancements for the safety and security of the Obsidian ecosystem:

- **Automated scans.** Every version is now automatically checked for code quality and security vulnerabilities. This includes malware scanning to detect potentially malicious additions to plugins. Developers can see detailed suggestions, warnings, and failure flags for every project in the developer dashboard.
- **Scorecards.** Users and developers can see the status of automated checks with scorecards on every project. These scorecards will continue to improve as we incorporate disclosures, privacy labels, artifact attestation, manual review results, and adoption of app capabilities.

Over the coming months, we will further increase transparency about plugins and their authors:

- **Disclosures.** Plugins will declare what they access: network, file system, clipboard, and other capabilities. Users will be able to see these disclosures before installing plugins.
- **Verified authors.** Labels will be added for trusted developers that have passed additional verification steps and are in good standing.

As a member of the Obsidian community you play a part in keeping the ecosystem safe. Users can always [flag security issues](https://obsidian.md/help/resources#Report+a+security+issue) directly to the Obsidian team.

## Tools for teams

Teams that use Obsidian can already [deploy safety controls](https://help.obsidian.md/teams/deploy) for their users. In the coming months we will make it easier for teams to manage which community plugins are allowed, and distribute **private plugins** to team members.

Teams that publish official Obsidian plugins can now apply for the [Official](https://community.obsidian.md/search?official=1) badge in the Community directory. [Reach out](https://discord.com/invite/obsidianmd) to us if your plugin qualifies.

## Next steps

As you can tell, there are many moving parts! Along with improvements to the Community directory and automated review system, we will also make changes to the Obsidian app and API to improve discovery and safety.

The community ecosystem is one of the most fun and powerful aspects of Obsidian. We’re excited to give it the foundation needed to continue flourishing.

We’d love for you to explore the new [Obsidian Community](https://community.obsidian.md/) and share your feedback with us!