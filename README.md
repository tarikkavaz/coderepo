### CODERepo - Collect Code Files into an HTML File

This script, `coderepo`, recursively finds code files in a specified 
directory and compiles their contents into a single file. 

The script is highly configurable, allowing users to specify file extensions, 
exclude certain extensions, ignore directories, and use a configuration file for default settings.

### Why?

When working on a project, it can be helpful to have a single file containing all the code files in a directory to send 
to LLMs to give them a better understanding of the project. This script automates the process of collecting code files.

#### Features

- Recursively find code files: Collect files with specified extensions from a directory and its subdirectories.
- Customizable extensions: Define which file extensions to include or exclude.
- Ignore directories: Specify directories to ignore during the search.
- Configuration file: Set default options in a config file following a .gitignore-like format.

#### Installation

1. Clone the repository: `git clone git@github.com:ekinertac/coderepo.git`
2. Change to the repository directory: `cd coderepo`
3. Install the script: `pip install -e .`
4. Run the script: `coderepo .`

> The project is under development and not yet available on PyPI. You can get the updates by pulling the repository.

#### Usage

Basic Usage

    coderepo .

This will search for code files in the current directory using most common programming language file extensions
and output an HTML file named `codereport.html` in the current directory.

> Note: The script will create a sample ignore file on first run located at ~/.coderepoignore


#### Options

- `-o, --output` : Specify the output HTML file name.
    coderepo . -o output.html

- `-e, --extensions` : List the file extensions to include.
    coderepo . -e .py .js .jsx

- `-x, --exclude-extensions` : List the file extensions to exclude.
    coderepo . -x .css .html

- `-i, --ignore-folders` : List the directories to ignore.
    coderepo . -i node_modules dist

- `-c, --config` : Specify a custom config file. Defaults to `~/.coderepoignore`.
    coderepo . -c /path/to/custom_config.txt

- `-f, --format` : The output format: yaml, json, xml, md, or html. Defaults to yaml.
    coderepo . -f html


#### Configuration File

The script can use a configuration file to set default options, allowing you to avoid specifying the same options repeatedly.

Default config file location: `~/.coderepoignore`

Custom config file: Specify with the `-c` option.

Config file format (similar to .gitignore):

- Extensions to include: List the file extensions directly.
- Extensions to exclude: Prefix with `!`.
- Directories to ignore: Prefix with `/`.

Example config file (`~/.coderepoignore`):

    # Extensions to include
    .py
    .js
    .jsx

    # Extensions to exclude
    !.min.js

    # Folders to ignore
    /node_modules
    /dist


### Example Extended Command

    coderepo . -o output.yml -e .py .js -x .html -i node_modules dist

This command will search for `.py` and `.js` files, exclude `.html` files, 
ignore the `node_modules` and `dist` directories, and generate an `output.yml` 
file in the current directory.

### TODO:

- [ ] Add testing for the script.


