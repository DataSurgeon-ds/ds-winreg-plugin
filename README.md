# ds-test-plugin
A DataSurgeon Plugin That is Used to Extract Numbers From Text

## How to Create a Plugin
All fields in the json object are required. If you are on windows the plugin file can be found here ```C:\ds\plugin.json```. The plugin file can also be stored in the current working directory (no matter the system). 
| Field          | Description                                                                                           |
|----------------|-------------------------------------------------------------------------------------------------------|
| content_type   | A one-word description of the content you are searching for (no spaces). This is the word that is going to be printed with the match                            |
| arg_long_name  | The argument name for the command-line interface. This must be unique across all plugins.             |
| help_message   | A brief description of what the plugin does. This will be displayed in the help message of the tool. |
| regex          | The regular expression used to match the content.                                                     |

```json
[
    {
        "content_type":"numbers",
        "arg_long_name": "numbers",
        "help_message": "Extracts numbers",
        "regex": "\\d+"
    }
]
```

## Example
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
drew@DESKTOP-A5AO3TO$ ds --numbers -f data.txt
numbers: 1
numbers: 2
numbers: 3
numbers: 4
numbers: 234
numbers: 2342342423566
numbers: 897871028031
```
