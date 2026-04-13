# CleverCoder Skills Catalog

Public skills catalog consumed by [CleverCoder](https://github.com/chamilonster) at runtime.

## What is this

`skills_catalog.json` is a curated list of Claude Code skills (community projects that extend what Claude can do inside a project). CleverCoder's "Nuevo Proyecto" wizard and the "Skills disponibles" window both read from this file.

On first launch, CleverCoder seeds its local cache at `%APPDATA%/CleverCoder/skills_catalog.json` from the built-in defaults. When its `_source` field points here, subsequent refreshes pull updates from this repo.

## File format

See `_schema` inside `skills_catalog.json` for field-by-field documentation. Short version:

```json
{
  "_readme":         "...",
  "_schema":         { "Id": "...", "Name": "...", ... },
  "_source":         "https://raw.githubusercontent.com/chamilonster/clevercoder-skills-catalog/main/skills_catalog.json",
  "_catalogVersion": 2,
  "skills": [
    {
      "Id":             "kebab-case-id",
      "Name":           "Display Name",
      "Description":    "English description with \\n line breaks.",
      "Category":       "Productivity|Development|Security|Organization|Content|Notifications",
      "Emoji":          "⚡",
      "GitHubUrl":      "https://github.com/owner/repo",
      "Author":         "owner",
      "Method":         "GitClone|NpxRun|OpenUrl|PluginInstall|PipInstall",
      "InstallCommand": "git clone ... / npx ... / /plugin install ...",
      "Commands":       ["cmd1", "cmd2"],
      "Source":         "community"
    }
  ]
}
```

## Contributing

Open a PR adding your skill to the `skills` array. Guidelines:

- English descriptions only — skills live in the English developer ecosystem.
- Include a valid `GitHubUrl` for the upstream repo.
- Pick the narrowest `Method` that works: prefer `GitClone` over `OpenUrl` when you can automate the install.
- `InstallCommand` should be copy-pasteable from a fresh shell.
- If the skill ships as a Claude Code plugin, use `Method: "PluginInstall"` and put the full `/plugin marketplace add` + `/plugin install` chain in `InstallCommand`.

## License

Catalog entries link to third-party repos with their own licenses. The JSON structure itself is released under the MIT license.
