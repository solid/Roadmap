# Solid Roadmap

The goal of this document is to act as a high-level overview of the broad topics that need proactive support / development to aid the adoption of Solid. This is largely designed to capture things that do currently have a repo/home to live under.

Open to contributions and comments.

## Proposed topics to address with priority within the CG
 - (Standardising) static client credentials
 - Standardising Query
 - Agreeing on the form of interop specs (hopefully, there will be some alignment in the STM)
 - Work on proposed standards changes for AP/Matrix alignment

Feedback loop from use cases: Support is needed to feedaback from lws-ucs and work taking place in the practitioners group.

## Development of Data Interop specs

One of the core promises of Solid has been to decouple applications from their data, thus allowing disparate Web applications to interoperate. That is, allowing such Web applications to share and re-use the same user data. To make this possible applications must have either (1) common data schemas or (2) data schemas between which there is a well-known mapping. This is a challenge that has also been identified by the NLnet-funded [Solid Application Interoperability work](https://nlnet.nl/project/Solid-Interop/). 

One potential work item towards the development of client-client specs is as follows:

*The infrastructure for managing a repository of shapes is mostly provided by Github. The pull request features and version control for managing code that comes with Github for free will allow us to save money that would have otherwise been spent on duplicating these features for our own proprietary platform. However, we will still need to build more features that github does not provide:*

*Project 1: Infrastructure*

* *Github Repo configurations*  
  * *A github organisation is set up with policies for submitting and approving new shapes.*  
  * *Templates to make the process of submitting new shapes as easy as possible are configured.*  
  * *A github action is triggered whenever shapes are approved that adds shapes to an external shape repository.*  
* *Creation of a Solid-based shape repository*  
  * *An instance of the community solid server is deployed to host shapes submitted to the github repo*  
* *Shape indexing*  
  * *An action is added to the github action that will take new shapes and add them to a search index*  
  * *An action is added to the github action that will take new shapes and push them to NPM*  
* *Search UI*  
  * *The UI for [https://shaperepo.com](https://shaperepo.com) is modified to handle SHACL shapes*  
  * *The data source of the search UI is updated to be the search index that shapes are added to during the shape indexing phase.*  
* *Shape creation guidelines*  
  * *A comprehensive list of guidelines and documentation is created to both guide would-be shape writers and to inform acceptance and rejection criteria for adding shapes to the shape repository.*

*Project 2: Creation of shapes for projects*  
*Develop shapes that describe the data model used by existing Solid applications such as SolidOS (https://github.com/SolidOS/solidos), Umai (https://umai.noeldemartin.com/), MediaKraken (https://noeldemartin.github.io/media-kraken/login) and SolidFlix (https://oxfordhcc.github.io/solid-media/) \- so as to ensure that future Solid applications are compatible with existing applications. As part of our best-practices we will also ensure that shapes for new Solid applications make use of popular existing vocabularies such as ogp ([https://ogp.me/](https://ogp.me/)), iCal, VCard, OFX, GPX and HL7 FHIR to facilitate interoperability with tooling external to the Solid ecosystem.*  
	*Bounties are paid for implementing shapes for a “complete use case.” For example, a “calendar” use case will require shapes for “calendars,” “events,” “participants,” “locations,” “times,” etc.*   
	*Depending on the complexity of the “complete use case” bounties will be between €1000 and €2000 for simply creating shapes and submitting them to the shape repository, and €2000 and €5000 for creating shapes, submitting them to the shape repository, and integrating those shapes into an application.*  
	*The priority for bounties will be for members of the Solid community, but if not enough community members opt to submit a bounty then the participants of this grant will generate shapes for common use cases.*

## Bootstrapping UI/UX development for Solid

Solid currently suffers from a lack of open-source applications with good looking interfaces / good UX. There are several threads that we can pursue to resolve this problem:

1. Taking existing open source applications and giving them a Solid “backend”. Logical domains to go for would be:  
   1. Chat: perhaps a matrix client like [cinny](https://github.com/cinnyapp/cinny).  
   2. … and all of the other clones available [here](https://github.com/GorvGoyl/Clone-Wars?tab=readme-ov-file).  
2. Making it easier to construct low-code Solid applications. Members of the Solid community have already approached this in several ways (e.g. Jeff Zuckers [Solid UI Components](https://github.com/jeff-zucker/solid-ui-components)) - however these are not like the stack that most current front-end developers are familiar with. We propose the following pathway to resolve this:  
   1. Support the creation of Solid components for [Webflow](https://webflow.com/apps). In particular for authentication, data fetching, rendering of basic things like profiles.  
   2. A replicable flow for app deployment e.g. using [vercel](https://webflow.com/made-in-webflow/vercel).  
   3. Support for developers to build Solid applications using Webflow. e.g funded or as a service
3. Improving the UX of existing applications such as:  
   1. SolidOS ([https://solidos.solidcommunity.net/](https://solidos.solidcommunity.net/))  
   2. Some of the applications listed [here](https://solidproject.org/apps).
4. Write integrations to make Solid accessible in the cases you commonly see Dropbox / GDrive, such as:
   1. The "locations" tab on your finder/file application on Mac or PC
   2. As a vscode extension (already started, but needs support https://github.com/jeswr/vscode-extension-solidfs)

Notes on the choice of platform:
 - Jackson M: I did a bit of research into webflow, and I'm not sure we'd be able to have a great Solid solution. From the looks of it, Webflow is mostly targeted at static stites. There is an add-on to Webflow called "Wized," that lets you build web apps with a backend. They have 4 options for backends (Airtable, Stripe, Canonic, Xano), and from what I can tell those are hard-coded. There's no way to add i/''
...add support for a new backend. There's no library or package system that we could put a Solid component on.
They do have the ability to implement REST calls from scratch, but the developer would need to manually do that.

## Education/onboarding materials for Solid
It is really hard to get and retain good developers working on Solid. There are many reasons for this, one of which is that there are poor training materials on how to get started in terms of navigating the community, developer materials etc. We need to develop a good onboarding flow for Solid in order to make it easier to bring in new talent at scale. This includes making it easy to bring on open-source developers who want to work on the projects at different time scales, e.g.:

- Here are the bugs you can work on if you’re not sure that you will be able to contribute for more than a couple of weeks  
- Here is how you can take a level of leadership in the project should you choose to (e.g. help provide ongoing maintenance to a core repo, triage issues etc.).

We are not the first project to be doing *any* of these things, IETF for instance has good processes that can be replicated.

Note that [this repo](https://github.com/solid/education) has been created as a place to collate educational materials for Solid.

## Opportunities: Integration with other efforts

Several communities have shared challenges. By aligning on the way these challenges are solved, we can improve the interoperability of different technology stacks and speed up Solid adoption.

**Authentication**: Part of the promise of Solid is Global Single Sign On. We can make a start by aligning Matrix, ActivityPub, etc. on the same authentication spec as Solid (possibly FedCM). Existing work in this domain includes:
 - https://forum.solidproject.org/t/real-world-use-cases/8369/8

## Integrations to aid adoption/use of Solid

To improve access to Pod data we need to have a concerted effort to build and maintain applications that make Solid available in locations where people typically integrate their drives.
It might be worth looking into market research to see what the most popularly used integrations of e.g. for GDrive are, and use those first.
 - A MacOS app to make your Solid storage available as a location on your machine - similar to this one for [Onedrive](https://apps.apple.com/gb/app/onedrive/id823766827?mt=12)
 - Implement Solid with the [Model Context Protocol](https://www.anthropic.com/news/model-context-protocol) to enable the claude model to access data in your Pod.
 - Maintain this VScode extension for accessing Solid: https://github.com/jeswr/vscode-extension-solidfs

## Support for research topics

Such as those listed [here](https://github.com/solid/research-topics)

## non-technical roadmap items
 - Establishing studentships to bring people students into the space

## Cataloging support
 - Get admin support to help maintian the [Solid Catalog](https://github.com/solid-contrib/catalog)
