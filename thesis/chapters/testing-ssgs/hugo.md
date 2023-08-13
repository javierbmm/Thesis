### Hugo

Hugo is a highly efficient, portable, and easy-to-use content management system that comes with a variety of design
themes.

As the testing environment is based on the Linux Debian distribution, one of the installation methods described on their
main website was chosen for this test, which was sudo apt install hugo.

However, it is important to note that there are multiple methods and sources for obtaining the Hugo framework, and each
has its own pros and cons, which are not discussed in this document because its primary purpose is to examine the
framework's primary features after installation.

To get started with Hugo, simply execute the following command `hugo new site new_site`. Hugo will create a folder with
the name of the project, in this case `new-site`, and a new theme can be added to this folder for styling. Notice that
there are a large number of already-created and freely-distributed themes, which saves you development time on styles
and aesthetics, you could install a theme (using `git submodule add [REPOSITORY NAME]`), add it to the Hugo
configuration file `config.toml`, and focus on adding content to the website.

Nonetheless, it is essential to recognize Hugo strategy's limitations. The first is the existence of paid themes, which
creates a financial gap within the open source community. This is understandable, however, as adding themes and
structures requires time, effort, and a certain level of understanding of the dynamics of user design and experience.

The second drawback is the added difficulty to modify a theme as the framework relies on **overriding** to change
specific configurations on styling, which obviously violates the SOLID principles in programming as per the inability to
extend these configurations wihtout overriding/changing the entire file, although this is not always applicable on
styling due to the intrinsic nature of how these are defined and approached in Web via CSS, however there is either a
straightforward method to perform tweaks to specific values, such as exposed variables which can provide the ability to
make changes within the same authored skeleton or component. For instance, exposing a variable that allows the user to
specify a desired padding between list entries, or a desired color for all secondary buttons.


