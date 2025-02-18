---
id: configuration
title: Bot Configuration
sidebar_label: Configuration
---

You can configure the all-contributors bot behaviour by updating the `.all-contributorsrc` JSON file.
The data used to generate the contributors list will be stored there, and you
can configure how you want `@all-contributors` to generate the list.

> You are viewing the 🤖Bot Configuration, which is similar to the [CLI Configuration](../cli/configuration)

These are the keys you can specify:

| Option                           | Description                                                                                         | Example/Default                                                                                             |
| -------------------------------- | --------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `files`                          | Array of files to update.                                                                           | Default: `['README.md']`                                                                                    |
| `imageSize`                      | Size (in px) of the user's avatar.                                                                  | Default: `100`                                                                                              |
| `contributorsPerLine`            | Maximum number of columns for the contributors table.                                               | Default: `7`                                                                                                |
| `contributorsSortAlphabetically` | `true`: Sort alphabetically. `false`: Display in order of addition.                       | Default: `false`                                                                                            |
| `badgeTemplate`                  | Define your own lodash template to generate the badge.                                              | |
| `contributorTemplate`            | Define your own lodash template to generate the contributor.                                        | |
| `types`                          | Specify custom symbols or link templates for contribution types. Can override the documented types. | |
| `skipCi`                         | Makes the CI ignore the commit. (either `true` or `false`)                                          | Default: `true` |
| `contributors`                   | List of contributors for this project, this is updated by [@all-contributors add](usage#all-contributors-add) | |

```json
{
  "files": ["README.md"],
  "imageSize": 100,
  "contributorsPerLine": 7,
  "contributorsSortAlphabetically": false,
  "badgeTemplate": "[![All Contributors](https://img.shields.io/badge/all_contributors-<%= contributors.length %>-orange.svg?style=flat-square)](#contributors)",
  "contributorTemplate": "<a href=\"<%= contributor.profile %>\"><img src=\"<%= contributor.avatar_url %>\" width=\"<%= options.imageSize %>px;\" alt=\"\"/><br /><sub><b><%= contributor.name %></b></sub></a>",
  "types": {
    "custom": {
      "symbol": "🔭",
      "description": "A custom contribution type.",
      "link": "[<%= symbol %>](<%= url %> \"<%= description %>\"),"
    }
  },
  "skipCi": "true",
  "contributors": []
}
```

#### Moving the All Contributors table into a different file

As you know, the default file for the contributors table is `README.md`. But if your project has tons of contributors, it doesn't make sense to include the All Contributors table in the `README.md` file. Instead, you can use a different file to do so.

Here are the steps that may help you in achieving that. For the sake of this tutorial, the different file that we'll use is going to be named `CONTRIBUTORS.md`.

1. Install the bot. See the [Installation](installation) page for instructions.
2. Add your first contributor. See the [Bot Usage](usage) page for instructions.
3. Create the `CONTRIBUTORS.md` file.
4. Copy the code which can be found in [this guide](installation#3-create-a-readmemd).
5. Modify the `files` key in the `.all-contributorsrc` JSON file to match your new file name.
   ```json
   {
   "files": [
      "CONTRIBUTORS.md"
   ],
   ...
   }
   ```
6. Now you should be good to go. New contributors will be added to this new file instead of the `README.md` file.
