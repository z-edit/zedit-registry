# zedit-registry
Registry for [zEdit](https://github.com/z-edit/zedit) themes and modules.  Users will be able to browse this registry and install themes and modules from it in zEdit in the near future. 

## entry requirements

In order for an entry to be added to this registry it must fit the following criteria:

1. Must have either a public GitHub repository or homepage.
2. It must be a zEdit module or theme.

If you want users to be able to install or determine the current version of your module/theme while browsing the registry it must have a public GitHub repository with at least one release.

In addition, if your repository is for a zEdit module it must have a top-level `module.json` file for requirements to be resolved correctly.

## adding entries

*NOTE: You must have a GitHub account to add or update entries.*

1. [Fork this repository](https://help.github.com/articles/fork-a-repo/).
2. In your fork, [edit](https://help.github.com/articles/editing-files-in-your-repository/) the `modules.json` file if you want to add a module.  Edit the `themes.json` file if you want to add a theme.
3. Add an [entry](#entry-data-format) at the end of the array for your module or theme.
4. [Create a pull request](https://help.github.com/articles/creating-a-pull-request-from-a-fork/).  Give your pull request a name in the format "Added \[Module Name\]", replacing \[Module Name\] with the name of the module you added.  If you added multiple modules list their names in sequence separated by commas.
5. If any of your entries don't meet the [entry requirements](#entry-requirements), you will be notified via a comment on your PR asking you to fix or remove them.
6. Once there are no issues with your PR it will be merged into the registry and will become visible to users browsing the registry immediately.

## updating entries

If you need to update a registry entry you can follow the same procedure enumerated for [adding entries](#adding-entries), but give your PR a name in the format "Updated \[Module Name\]".

## entry data format

The registry is stored as plaintext [JSON](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON) files.  There are two files, `modules.json` for modules and `themes.json` for themes.

Entries must have all of the following properties unless otherwise noted.

### `id`

The unique identifier for your module or theme.  For modules this should be the `id` specified in your `module.json` file.  For themes this should be your theme's compiled filename without the `.css` extension.

### `name`

The name of the module or theme.  This does not need to be unqiue.

### `types`

**For module entries only.** Array of one or more values from this list:

- `"api"` - Modules which provide one or more APIs to be consumed by other modules or user scripts.
- `"tool""` - Modules which provide a tool or toolset to be used within an existing application mode.
- `"patcher""` - Modules which generate dynamic patch plugins (usually through UPF).
- `"appmode"` - Modules which provide an entire application mode.

### `games`

**Optional.  For module entries only.** Array of game modes your module supports.  Omit if your module does not have any game-dependent code.  Game mode strings:

- `"TES5"` - The Elder Scrolls V: Skyrim
- `"SSE"` - Skyrim: Special Edition
- `"FO4"` - Fallout 4
- `"FNV"` - Fallout: New Vegas
- `"FO3"` - Fallout 3
- `"TES4"` - The Elder Scrolls IV: Oblivion

### `description`

A short plaintext description for your module or theme.

### `links`

Object containing links where the module can be downloaded.  The following keys are currently supported:

- `"github"` - GitHub repository URL
- `"nexus"` - Nexus Mods mod page URL
- `"nexus-2"` - Secondary Nexus Mods mod page URL
