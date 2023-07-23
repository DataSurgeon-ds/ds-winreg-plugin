# Welcome to ds-test-plugin
A guide to create your own plugins for DataSurgeon

## Jump Right In
- [Find Your Plugin File](#find-your-plugin-file)
- [Creating Your Own Plugin](#creating-your-own-plugin)
- [How to Use Your New Plugin](#how-to-use-your-new-plugin)


## Find Your Plugin File
We've got you covered whether you're using Windows or Linux. If you're a Windows user, you'll find the plugin file in the  `C:\ds\` directory. If you're on Linux, look for the plugin file here: `~/.DataSurgeon/plugins.json`. And if by chance the plugin file isn't found in either of these directories, we'll automatically check the current working directory.

## Creating Your Own Plugin
Every field in the json object is important. To ensure your plugin works seamlessly with the DataSurgeon options `--add` and `--remove`, remember to upload your `plugins.json` file to a GitHub repository. Please make sure the filename remains as `plugins.json` and only include the plugin options you wish to upload. Here's a quick guide to the fields:

| Field          | Description                                                                                           |
|----------------|-------------------------------------------------------------------------------------------------------|
| content_type   | This should be a one-word description of the content you're searching for (no spaces). This is the word that gets printed alongside the matched content.                            |
| arg_long_name  | This is the unique argument name for the command-line interface. It must be unique across all plugins.             |
| help_message   | This is a short and sweet description of what your plugin does. It'll appear in the help message of the tool. |
| regex          | This is the regular expression that's used to match the content. To ensure compatibility with the `--clean` option, your regex should be designed such that the entire match `($0)` contains the exact content you're interested in. This allows the `--clean` option to extract only the relevant matched content. For testing your regex patterns, we recommend using https://regexr.com/|
| source_url | This is the URL to the GitHub repository hosting your plugin | 

Here's an example:

```json
[
    {
        "content_type": "numbers",
        "arg_long_name": "numbers",
        "help_message": "Extracts numbers",
        "regex": "(\\\\d+)",
        "source_url": "https://github.com/Drew-Alleman/ds-test-plugin/"
    }
]
```
## How to Use Your New Plugin
Once your plugin file is loaded, the option will be added as an additional argument.
```
drew@DESKTOP-A5AO3TO$ ds -h

Options:
   ......
  -a, --aws                    Extract AWS keys
      --numbers                Extracts numbers
  -V, --version                Print version
```
And here's how you can run it:
```
C:\Users\DrewQ\Desktop\DataSurgeon\target\release>ds.exe --numbers -f data.txt --clean
numbers: 1
numbers: 2
numbers: 3
numbers: 4
numbers: 234
numbers: 2342342423566
numbers: 897871028031
```
