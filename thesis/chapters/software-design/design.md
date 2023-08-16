# Software Design

## Overview

The VaGo Static Site Generator, as presented in this project, is designed to be utilized by fellow developers for the
purpose of creating straightforward and user-friendly websites, prioritizing content over any additional functionalities
offered by the site. Hence, the paramount consideration lies in the user-friendly nature of VaGo, which allows for
enhanced concentration on content during usage.

In this manner, VaGo should possess the capability to parse markdown files and convert them into web pages.
Additionally, it should be able to serve this content through a designated port, while implementing automatic routing
based on the file name to URL convention. Furthermore, VaGo should ensure that the user remains informed about each step
executed by the Static Site Generator (SSG) through consistent and informative logging.

Therefore, the design of VaGo is significantly dependent on and focused on the following essential elements: Parse,
construct, serve, route, and log. This section will now propose a recommendation for the implementation of these
components and an approach to construct their interconnection, in accordance with fundamental programming principles,
with the aim of developing software that exhibits both robustness and maintainability. It is important to acknowledge
that the content presented in this chapter is merely a proposal, subject to potential changes or modifications
throughout the implementation phase. This flexibility is necessary as additional challenges and requirements may emerge. 

