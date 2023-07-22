# ds-test-plugin
A DataSurgeon Plugin That is Used to Extract Numbers From Text. 

## Quick Links
WIP

## Plugin File Location
If you are on windows the plugin file can be found in the  ```C:\ds\``` directory. If you are Linux the plugin file can be found here: ```~/.DataSurgeon/plugins.json```. If the plugin file is not found in either of these directories it will check the current working directory.

## How to Create a Plugin
All fields in the json object are required. In order for your plugin to work with the DataSurgeon option ```--add``` and ```--remove``` you need to upload your ```plugins.json``` file to a github repository. (the filename needs to be ```plugins.json``` and please ONLY include the plugin options you want to upload)
| Field          | Description                                                                                           |
|----------------|-------------------------------------------------------------------------------------------------------|
| content_type   | A one-word description of the content you are searching for (no spaces). This is the word that will be printed alongside the matched content.                            |
| arg_long_name  | The argument name for the command-line interface. This must be unique across all plugins.             |
| help_message   | A brief description of what the plugin does. This will be displayed in the help message of the tool. |
| regex          | The regular expression used to match the content. To ensure compatibility with the ```--clean``` option, your regex should be designed such that the entire match ```($0)``` contains the exact content you're interested in. This allows the ```--clean``` option to extract only the relevant matched content. You can test your regex patterns with https://regexr.com/|


```json
[
    {
        "content_type":"numbers",
        "arg_long_name": "numbers",
        "help_message": "Extracts numbers",
        "regex": "(\\d+)"
    }
]
```

## Example Usage
When the plugin file is loaded the option will now be added as an additional argument
```
drew@DESKTOP-A5AO3TO$ ds -h

Options:
   ......
  -a, --aws                    Extract AWS keys
      --numbers                Extracts numbers
  -V, --version                Print version
```
Now to run it
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
