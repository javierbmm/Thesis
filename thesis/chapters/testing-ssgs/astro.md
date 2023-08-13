### Astro

Astro promotes itself as an all-in-one web framework, as opposed to a simple static site generator, despite serving the
same purpose with full batteries features specialized to focus on content creation and management rather than pure
development, and designed to be fast and performant.

To utilize it, simply visit their website (_http://astro.new_) to play with a fully functional browser version of Astro.
Similarly, to use it in a local environment, NodeJS and `npm` are required, and a new project will be created using `npm
create astro@latest` to begin development.

In contrast to other Single Page Application frameworks where everything is loaded at client-side, and most server-side
render applications where it takes a considerable amount of time to load the page when the project starts growing, Astro
uses a Partial Hydration, which means that the content (which is always, or at least it will try to always render it in
the server) is only loaded when it is needed. For example, some content can be loaded concurrently with scrolling once
it becomes visible in the browser.

This method, in conjunction with the island architecture, which divides the website into distinct sections, enables the
framework to have significantly improved performance compared to other methods.

Therefore, Astro focuses on the serving sites' performance, allowing the developer to focus on content creation without
worrying about execution details, while providing several features to customize the serving process and also enabling
the customization of the working environment as it has hundreds of integrations to choose from, such as front-end
frameworks (being framework agnostic in the sense that it does not rely on any particular tool), preprocessing toolings,
such as Sass, and so on.

Finally, Astro is a highly effective framework with numerous customization options from which to study. It allows for a
great deal of freedom and flexibility while remaining simple to use. Nevertheless, for a simple static site generator it
may be an overkill tooling system to use, as it is designed to compete against single page applications with their
multiple page application approach, and it lacks an opinionated or strict structure to adhere to, which makes sense as 
it must fulfill the needs of a complete website.
