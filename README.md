### HTMLRepo - Collect Code Files into an HTML File

This Python script, `htmlrepo`, recursively finds code files in a specified 
directory and compiles their contents into an HTML file. 

The script is highly configurable, allowing users to specify file extensions, 
exclude certain extensions, ignore directories, and use a configuration file for default settings.

#### Features

- Recursively find code files: Collect files with specified extensions from a directory and its subdirectories.
- HTML output: The contents of the found files are compiled into a single HTML file for easy viewing.
- Customizable extensions: Define which file extensions to include or exclude.
- Ignore directories: Specify directories to ignore during the search.
- Configuration file: Set default options in a config file following a .gitignore-like format.

#### Installation

1. Create a file named htmlrepo in a directory of your choice `touch htmlrepo`
2. Copy the script content into the htmlrepo file.
3. Make the script executable: `chmod +x htmlrepo`
4. (Optional) Move the script to a directory in your PATH (e.g., /usr/local/bin) `sudo mv htmlrepo /usr/local/bin/`
5. Verify the installation `htmlrepo --help`

#### Usage

Basic Usage

    htmlrepo .

This will search for code files in the current directory using most common programming language file extensions
and output an HTML file named `htmlreport.html` in the current directory.

#### Options

- `-o, --output` : Specify the output HTML file name.
    htmlrepo . -o output.html

- `-e, --extensions` : List the file extensions to include.
    htmlrepo . -e .py .js .jsx

- `-x, --exclude-extensions` : List the file extensions to exclude.
    htmlrepo . -x .css .html

- `-i, --ignore-folders` : List the directories to ignore.
    htmlrepo . -i node_modules dist

- `-c, --config` : Specify a custom config file. Defaults to `~/.htmlrepoignore`.
    htmlrepo . -c /path/to/custom_config.txt

#### Configuration File

The script can use a configuration file to set default options, allowing you to avoid specifying the same options repeatedly.

Default config file location: `~/.htmlrepoignore`

Custom config file: Specify with the `-c` option.

Config file format (similar to .gitignore):

- Extensions to include: List the file extensions directly.
- Extensions to exclude: Prefix with `!`.
- Directories to ignore: Prefix with `/`.

Example config file (`~/.htmlrepoignore`):

    # Extensions to include
    .py
    .js
    .jsx

    # Extensions to exclude
    !.css

    # Folders to ignore
    /node_modules
    /dist

Example Command

    htmlrepo . -o output.html -e .py .js -x .html -i node_modules dist

This command will search for `.py` and `.js` files, exclude `.html` files, 
ignore the `node_modules` and `dist` directories, and generate an `output.html` 
file in the current directory.

License

This project is licensed under the MIT License. See the LICENSE file for details.