## Introduction

### Purpose

The primary objective of this chapter, which is referred to as the Software Requirements Specification (from this point
forward, SRS), is to define the requirements and, as a result, the goals that need to be accomplished by the Static Site
Generator that is described and implemented throughout the entirety of this project. This will be accomplished by
providing a detailed explanation of how the system as a whole works as well as the various components that make up the
system.

The person in charge of the creation of the SSG, the developer and/or implementer, is the intended audience for this
SRS. Given that it outlines the considered implementation details and design specifications, it serves as a guide for
the developer to know exactly what to do along with the definition of done for each task and/or component.

### Scope

The Static Site Generator described in the document will be known as `VaGo`, and will henceforth be referred to as such.
The nomenclature of this tool is derived from its implementation in the Go programming language, as expounded upon in
subsequent sections. Additionally, the name incorporates a homograph word in Spanish, "vago," which connotes indolence
or sloth in English. This serves as a playful allusion to the minimal exertion demanded of prospective users in
generating a static website through utilization of this software.

VaGo is a tool designed to facilitate the creation and distribution of static content on the web. Its primary function
is to interpret and translate markdown files into web content, which includes HTML, CSS, and necessary JavaScript.
Furthermore, the system will facilitate the implementation of a theming mechanism, which will enable the creation and
dissemination of particular style guidelines for reuse and adherence by the content after its translation from markdown.
This theming system will also allow for a flexible and open approach to effectuate specific author-provided
modifications to the style of the pages, such as the inclusion of particular padding between elements, the adjustment of
text size based on the heading hierarchy, the selection of colors, the application of specific button styles, and other
customizable features, which will be contingent upon the preferences established by the theme author.

The provision of flexibility enables prospective users of designated themes to make necessary adjustments to suit their
individual requirements, without the need of extensively search through the styling boilerplate and navigating through
numerous CSS files to locate the particular parameter to modify.

Similarly, VaGo will offer a straightforward command-line interface (CLI) to facilitate interaction with the program to
serve the purpose of translating content into static web pages. This will be possible once the content has been provided
in the form of markdown, along with theme styling. Additionally, VaGo will enable users (via the command line) to serve
the content as websites through a specified port, using Go's native HTTP methods.

Conversely, the system won't offer support for alternative interpretation formats, such as YAML or JSON, nor can be
expected it facilitates the translation of Go code to JavaScript or vice versa. Hence, it is not to be anticipated that
it would provide backing for JavaScript reactivity, akin to what is observed in other front-end frameworks. VaGo will
exclusively restrict its capabilities to the delivery of static content through fundamental and native CSS and
JavaScript. Its primary objective is to facilitate the development process, with a singular focus on this goal to ensure
optimal performance. This approach aims to alleviate the burden of web development for individuals who seek to share
text or images without delving into the intricacies of the field.

### Definitions, acronyms and abbreviations.

* SSG: Static Site Generator.
* MD: Markdown files.
* JS: Javascript.
* CSS: Cascading Style Sheets.
* HTML: HyperText Markup Language.
* CLI: Command-line interface.
* Theme/Style theme(ing): A set of established reusable guidelines and rules to provide style to the web content
  (website) via HTML and CSS for the sake of consistency.

### References

The following collection provides a selection of research documents aimed at facilitating comprehension of the
foundational principles that motivate the prerequisites for VaGo. Emphasis is placed on elucidating the rationale behind
the necessity of these requirements.

* _What is a static site generator?_. Cloudflare. (n.d.)
  . https://www.cloudflare.com/learning/performance/static-site-generator/
* Khalid, F. S. (2022, April 18). _How to choose the right static site generator_.
  GitLab. https://about.gitlab.com/blog/2022/04/18/comparing-static-site-generators/
* Wikimedia Foundation. (2023, August 12). _Static Site Generator_.
  Wikipedia. https://en.wikipedia.org/wiki/Static_site_generator
* Wikimedia Foundation. (2023a, April 11). _Hugo (software)_. Wikipedia. https://en.wikipedia.org/wiki/Hugo_(software)
* _What is Hugo_. Hugo. (2023, July 13). https://gohugo.io/about/what-is-hugo/
* _Docs. What is Next.js_. Next.js. (n.d.). https://nextjs.org/docs
* _VuePress guide. Introduction_. VuePress. (n.d.). https://v2.vuepress.vuejs.org/guide/
* _Accessibility principles_. Web Accessibility Initiative (WAI)
  . https://www.w3.org/WAI/fundamentals/accessibility-principles/
* MozDevNet. (n.d.). _What is accessibility?_ Learn web development |
  MDN. https://developer.mozilla.org/en-US/docs/Learn/Accessibility/What_is_accessibility
* MozDevNet. (n.d.-a). _HTML: A good basis for accessibility._ Learn web development |
  MDN. https://developer.mozilla.org/en-US/docs/Learn/Accessibility/HTML
* Sun, Y. (2019). _Server-Side Rendering. In: Practical Application Development with AppRun_. Apress, Berkeley,
  CA. https://doi.org/10.1007/978-1-4842-4069-4_9
* Taufan Fadhilah Iskandar et al (2020). _Comparison between client-side and server-side rendering in the web
  development_ https://iopscience.iop.org/article/10.1088/1757-899X/801/1/012136/pdf

### Overall description

This chapter comprises several sections that present a series of requirements according to certain demands. These
requirements are derived from an analysis of existing tool scopes, previous work conducted on these tools, potential
areas for improvement under specific conditions, the current state of web development, and key considerations for
enhancing the user experience.

Subsequently, the requirements are presented in a structured manner, delineating the essential aspects of these
requirements, including the intended input and output, the format in which these capabilities are being built, and the
precise requisites for each individual functionality.

Therefore, the primary objective of this section is to present a comprehensive list of explicit requirements associated
with the functionalities to be developed. These requirements will be supported by detailed explanations and
justifications for their necessity. The aim is to establish a solid and comprehensive set of needs, prioritized
according to their importance. This will facilitate a better understanding of the development tasks required to consider
the project as completed.







