## VuePress

VuePress is self-defined as a minimalistic static site generator, powered by Vue to build the theme system, optimized to
focus on content creation such as technical documentation via markdown files for metadata, content, configuration, and
more. It renders pages with static HTML and turns the page to a Single Page Application.

In order to use it, NodeJS and Vue are required. Once these dependencies are up-to-date, one can start creating and
working on a site by using the Node CLI command `npx create-vuepress-site [optionalDirectoryName]`, and it will ask for
further information on the site such as project name, description, and more.

Once done, it will create a basic documentation site under the `docs` folder. In order to see the website live, the Node
modules within `docs` must be installed: `npm install`, and then it can be served locally doing `npm run dev`.

The development experience with VuePress is generally undemanding, as it handles all tasks required to build a website,
leaving the emphasis on the content creation via markdown files, and the static content (images, videos) integration is
also seamless, as all that is required is to leave them in a given folder and specify the media path within the config
markdown, while the theme handles all styling and structure.

However, the themes depend on the Vue framework, which adds an additional layer to the learning curve, and the theme
styling can be exposed as variables following the config structure, although the developer has total control over how
this structure is organized. The issue with this approach is that it makes it difficult to learn different themes, as
each author is free to organize them as they see fit, and one must put in the time and effort to comprehend the theme in
order to make further customizations. The lack of established and opined structure may result in disorderly
configurations, but this is the price of such freedom.

After using VuePress and NextJS, it is important to note that using NodeJS as a package and dependencies manager
increases the developer's pain and work load. NodeJS is notorious for causing pain among developers due to the
complications it can lead to when a dependency is not met or is out-of-date, as the solution is never straightforward
and further investigation is required to determine what could be happening in t. During this testing, conflicts between
the NodeJS version and the VuePress required dependencies caused a number of issues.

