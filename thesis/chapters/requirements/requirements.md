## Specific requirements

### External interfaces

Users will be able to interact with the system using CLI commands to carry out simple operations that are built into the
system. Here, two fundamental commands should be noted:

* `Build`.
* `Serve`: To serve and share content via a specific port.

Additionally, the system ought to alert the user any time a command it has issued contains an error because it is
possible for them to accidentally type the wrong command or misspell any of these. (using buidl instead of build).
Notably, unlike other systems, it will lack a recommendation system to offer hints of similar words that are actually
interpreted as to assist the user in finding alternative commands, even though it will inform the user about the
existence of an error that prevented the system from performing the required task.

#### Build

The task at hand involves the conversion of Markdown files into web-based content, specifically in the form of HTML, JS,
and CSS.

The program is designed to utilize the Command Line Interface (CLI) as an input mechanism, whereby it recognizes the
command name to execute its designated task. Its output function involves generating the HTML and CSS content into an
`out` folder, in accordance with the pre-existing Markdown files. It is noteworthy that each MD file ought to generate
an individual page to allow for the adaptability of transforming every file into a distinct output for the website.

Throughout the translation process, it is imperative that the user is kept informed of its progress. In the event of any
errors, the system should prompt error messages to ensure the accuracy of the MD files, while simultaneously verifying
that all necessary parameters for content and styling have been provided. Upon completion, the system should explicitly
indicate the out folder path to the user.

Therefore, it should use the following format for each of the steps considered for the translation and building process:
[Date][Page Name]: Step, where each one of these detail token corresponds to:

* Date: Specific date and time using the ISO 8601 format [1](https://en.wikipedia.org/wiki/ISO_8601) without specifying
  the timezone as `VaGo` will limit itself to use the same timezone from the host machine. For instance: _2023-04-09T14:
  22:05_
  should be used to represent the year 2023, month April (04), day 09 at 14 hours, 22 minutes and 05 seconds.
* Page Name: To specify the exact page name for the URL that takes to that specific page, which is the same as the MD
  file name.
* Step: To specify the building step it's currently on, whether it is identifying the MD tokens, performing translation
  to HTML and/or obtaining the parameters set for the theming and styling of the given page.

On the other hand, additional parameters can be added to the command for specific output capabilities. For instance,
`no-log` should be using to omitting logging (no prompt message for every building process step) except for error and
finalization message. Also, `no-time` should be used to omit the timestamp from the steps, prompting a message with the
following structure: _[Page name]:Step_, with the purpose of avoiding overloading logs and make them easier to read.

#### Serve

The second command serves the purpose of keep the system continuously executing, hence no accepting other commands in
the meantime, in order to open a port and send the already built files (by means of the previous command, `build`) via
HTTP.

It is important to note that this command will exclusively serve content available in the `out` folder, therefore if the
previous command hasn't been run, or if there are no files in this folder, then it won't be able to serve any content at
all. Because of it, it is required that the user must first build content in order to then serve it.

Moreover, in addition to the behavior noted above, it must output logs to inform the user of the current status of the
serving process, starting by indicating as soon as it starts reading content and initiating listening for requests,
while also informing of any issue that may occur by prompting error messages.

Once it starts listening for requests, it should inform of any incoming request/response using the following format:
[Date]: Sending [Page] to [requester IP], where each one of these token corresponds to:

* Date: Same as the one outlined for `build` command, using the ISO 8601 format without timezone.
* Page: Page name as stated in the MD filename.
* Requester IP: Specific IP address of the incoming IP.

Additionally, an extra (optional) parameter can be provided to outline the specific port the system should open to
listen for requests, instead of the default one.

### Functions

The following provides a more in-depth explanation of the functional areas, including full requirements.

#### Generate page

##### Description and priority

The task at hand involves generating a page document through the process of translating the contents of a Markdown file
into HTML. This requires the utilization of appropriate tags to accurately map the entities present within each Markdown
block. Priority: HIGH.

##### Stimulus/Response sequences

Stimulus: This feature must obtain the markdown files from a `source` folder.

Response: Translate or generate a corresponding HTML file for each one of these MD files, outputting the result pages
into an `out` folder.

##### Functional requirements

**REQ-1**: The MD blocks must be interpreted and translated to HTML tags to generate a page accordingly to what the user
has described initially. It should, at least, implement the following elements to ensure a fully accessible page as per
best practices for web standards:

* Heading level 1 (`#`): Heading 1 (`<h1></h1>`).
* Heading level 2 (`##`): Heading 2 (`<h2></h2>`).
* Heading level 3 (`###`): Heading 3 (`<h3></h3>`).
* Heading level 4 (`####`): Heading 4 (`<h4></h4>`).
* Heading level 5 (`#####`): Heading 5 (`<h5></h5>`).
* Heading level 6 (`######`): Heading 6 (`<h6></h6>`).
* Text: Paragraph (`<p></p>`).
* Bold text (`**text**`): Strong (`<strong></strong>`).
* Italic text (`_text_`): Emphasis (`<em></em>`).
* Blockquote (`>`): Blockquote (`<blockquote></blockquote>`).
* Unordered list (`-`): Unordered list (`<ul></ul>`) surrounding list items (`<li></li>`).
* Ordered list (`1.`, `2.`, `3.`, and so): Ordered list (`<ol></ol>`) surrounding list items (`<li></li>`).
* Code (` `` `): Code (`<code></code>`).
* Fenced code block (` ``` ``` `): Preformatted text (`<pre></pre>`) surrounding a code block (`<code></code>`).
* Link (`[text](URL)`): Anchor tag along with the hyperlink attribute (`<a href="URL">text</a>`).
* Image (`![Alt text](URL)`): Image tag along with alt text and source
  attributes (`<img alt="Alt text" src="URL"></img>`).

**REQ-2**: It must verify whenever there is an input error or incorrect usage of the MD blocks, and thereby let the user
know about these via error messages and halt the translation process immediately.

**REQ-3**: Each generated page will have the same file name as the input MD file.

#### Theme styling creation and customization

##### Description and priority

This feature is responsible for enabling the construction of a customizable theme for styling purposes. As long as the
author (the theme creator) enhances these capabilities via exposed variables, it will manage CSS files that will provide
styles to the pages and provide functionalities to perform tweaks and changes to the theme. Therefore, subsequent users
of the same theme would be able to make certain modifications to suit their needs, while retaining the already provided
set of opinionated styles. Priority: MEDIUM.

##### Stimulus/Response sequences

Stimulus: Single or multiple files with preprocessed CSS attributes that will receive the values of the exposed
variables to be processed into a final CSS file. Notice that the format of this file is not strictly CSS as it should be
noted that it is waiting for the building stage to add the variables, therefore it's suggested to use a temporal file
name adding `.go.css` to differentiate it from its final version.

Response: Once processed, the file or set of files will be merged into a single one, following an established structure
and adding the exposed variables via Go.

Stimulus: Authored parameters in the form of Go variables. There is also the possibility of exposing such variables via
YAML or JSON format, to avoid overwriting Go code.

Response: The parameters are added to the final CSS file.

**REQ-1**: The exposed parameters should be added within the preprocessed style file using the
pattern `${[variable name]}` in the same place where it will be replaced.

**REQ-2**: These variables are then added or modified within a specific Go module specifically designed for this
purpose. Thereby, the author will be able to expose these in this file, and add a default value in case the user decides
to not change anything. It should be noted that the system won't take care of the compilation or verification of the CSS
file, hence it is completely up to the author to verify whether it is correctly built.

**REQ-3**: Multiple style files could be added together in a single final one, providing the author the flexibility to
split them into different modules for readability and maintainability purposes, thus these must be specified in a Go
module specifically designed for this purpose, or within a main preprocessed style file using the nomenclature
`${#module: [file name]}`.

**REQ-4**: The system must verify and prompt a clear error message when there is a theme variable that has not been set.
More specifically, it should display a message using the following structure: "_Error: [variable name] has not been
initialized._", where the variable name will be replaced with the specific variable missing its initialization.

#### Templating

##### Description and priority

The proposed system will incorporate a functionality that enables the establishment of a predetermined framework or
outline, in addition to the primary template, for organizing the content into web pages. It is noteworthy that the
utilization of Go language's templating capabilities is integral to the handling of this task. However, the system must
furnish a mechanism for retrieving the primary information components from the markdown files. This will enable easy
recognition and referencing of said components in the template, thereby facilitating customization. Priority:
MEDIUM.

##### Stimulus/Response sequences

Stimulus: Single or multiple HTML files with Go templating variables to be filled with, from which the user can decide
to use custom variables (from custom Go code) or the main, already provided variables from the markdown file components
(headings, text, bold, italic, lists, etc).

Response: When built, a final HTML file should be prompted with the provided content via markdown files and following
the provided structure or skeleton as in the template.

##### Functional requirements

**REQ-1**: The processed format must follow the established skeleton from the template. If there is no provided
template, the system must use a base one already provided with the generator.

**REQ-2**: Each markdown component should be accessible via Go variables following this naming convention:

* Heading level 1 (`#`): `H1`
* Heading level 2 (`##`): `H2`.
* Heading level 3 (`###`): `H3`.
* Heading level 4 (`####`): `H4`.
* Heading level 5 (`#####`): `H5`.
* Heading level 6 (`######`): `H6`.
* Text: `B`.
* Bold text (`**text**`): `Strong`.
* Italic text (`_text_`): `Em`.
* Blockquote (`>`): `Blockquote`.
* Unordered list (`-`): `Ul`.
* Ordered list (`1.`, `2.`, `3.`, and so): `Ol`.
* Code (` `` `): `Code`.
* Fenced code block (` ``` ``` `): `Pre`.
* Link (`[text](URL)`): `A`, `A.URL`.
* Image (`![Alt text](URL)`): `Img`, `Img.Alt`, `Img.Src`.

It is important to note that the naming convention and HTML elements are identical. This is intentional, as it should
direct the user to the correct element the component should be used in, so as to maintain best practices for web
accessibility and search engine optimization, avoiding the use of meaningless `div` tags everywhere.

#### Configuration files

##### Description and priority

Through the configuration files the user will be able to set up certain parameters that will change the way the system
works to adapt it to given needs and setup, such as determine specific input and output folders, theme name, template
file name, author information (name, website name, creation date), and others. It's worth noting that these
configuration files are not strictly necessary as the system must initiate with a set of given default parameters, which
can be overwritten for extended customization. Priority: LOW.

##### Stimulus/Response sequences

Stimulus: A Go, JSON or YAML file with the set of parameters to be read from, so the system can use them as variables
for its configuration. The type of file to be used will depend on the development time, as reading directly from a Go
file or module it's easier and faster to implement than a JSON or YAML file, as it requires a parsing step first.

Response: The system will produce and/or build the static content following these parameters accordingly.

##### Functional requirements

*REQ-1*: The system will use a set of default values if the configuration files are not provided/changed, thus it is not
strictly needed for the system to work properly.

*REQ-2*: The following configuration files must be scanned (found via specific filename) and used for its respective
purpose: Theme config (`theme.*`, ) to specify styling parameters as well as the theme name, template config (`
layout.*) to specify the files entries for templating, main configuration (main.*) for the main parameters for VaGo.
File extension to be decided depending on development time as noted on previous point.

*REQ-3*: For each configuration file, the system must be able to interpret and apply the following parameters:

1. Theme config (`theme.*`):

* Theme name (`name`): The name of the given theme. This name will be accessed for further setup steps. 
* Parameters(`params`): An open field to add a list of the open parameters for styling.

2. Template config (`layout.*`): 
* Entries (`entries`): A list of template filenames to be included in the templating system. 
* Final layout (`final`): A nested ordered list of the templates to be merged for the final composition layout. 

3. Main config (`main.*`):
* Author name (`author`): The author name of the website to generated content for. 
* Input folder (`input`): Input folder to get the files to read content from, prior to the website generation.
* Output folder (`output`): Output folder to write the static generation results.
* Theme (`theme`): The name of the theme to be used for this website.

It is worth noting that these configuration files and parameters are not final, and yet other may get included in the
future depending on the needs that may arise. 




