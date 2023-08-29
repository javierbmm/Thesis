# Used technologies

This section will present a review of the external technologies, modules, and frameworks that have been incorporated
into the project. These components have been interconnected to address specific issues, streamline the development
process, and meet the defined requirements.

## gomarkdown

_https://github.com/gomarkdown/markdown_

External Go module that provides enhanced features to extract the content of a markdown file in tokens following the
Abstract Syntax Tree from the file, useful with the extraction that are included within other tokens. For instance, a
bold text that is within a bigger piece of text from a list.

This is useful as the context is preserved and can be then used to follow a given structure from the provided template
at the generation stage, providing both flexibility and ease to use for the end user.

It is important to note that this same library provides also functionalities to automatically parse markdown files to
HTML. However, this is not used in the project given that it provides limited flexibility, and it does not capabilities
to produce HTML from a provided template, which is one of the main functionalities of VaGo. Similarly, it does not have
any HTTP service to serve and route requests.

Therefore, this module is only meant to be used in the Parser stage on the information extraction step, with pertinent
modifications to adapt it to VaGo requirements.

## Go standard libraries

Multiple modules from the Go standard have been used in the implementation of this project, as it has been limited to
the usage of standard libraries as much as possible to avoid overloading from external sources, which are prompt to
unexpected changes and failures.

It is important to note that this section is not meant to go through all the modules available and used during the
development of this project, as most of them provide trivial functionalities such as string formatting, but some of the
most important modules that provides functionalities required for the development of VaGo, which would require extended
amount of time to develop otherwise, and are not the main focus of this project.

### HTML/Template

_https://pkg.go.dev/html/template_

The package template (html/template) is designed to facilitate the creation of data-driven templates that generate HTML
output. These templates are specifically designed to mitigate the risk of code injection, ensuring the security of the
resulting HTML content. The package in question offers an interface that is identical to that of text/template.
Therefore, it is recommended to utilize this package in favor of text/template whenever the desired output is in the
form of HTML.

Moreover, by means of this package, VaGo can provide extended flexibility and customization capabilities to the end user
when creating their own site implementing their desired skeleton and structure to be followed by the markdown content.

### Go YAML

_gopkg.in/yaml.v3_

The third iteration of the YAML package for the Go programming language introduces enhanced functionality enabling
effortless encoding and decoding of YAML files.

The primary purpose of this tool is to extract the values from configuration files and organize them into predefined
structures. These structures are subsequently utilized to get specific information needed for various activities,
including input and output folder management.

## urfave/cli

_https://github.com/urfave/cli_

This package provides a straightforward and user-friendly solution for constructing Command Line Interface (CLI) tools
in the Go programming language. It has several features, including the ability to add commands and subcommands, support
for alias and prefix matching systems, an automatically created help system with documentation in markdown format, and
additional functionalities.

The purpose of this package is to facilitate the construction of VaGo as a command line tool. It accomplishes this by
implementing commands for the Build and Serve stages, which include input arguments, flags, and a help command to offer
guidance on usage. The package aims to provide a straightforward implementation and usage experience for the end user.
Additionally, it serves as a convenient method for installing VaGo on the user's system.

## HTTP 

