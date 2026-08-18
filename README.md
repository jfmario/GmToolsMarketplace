
# GM Tools Marketplace

This marketplace repository hosts Claude plugins relating to tabletop RPGs, particularly for game masters.

## Getting Started (Claude)

### User Scope

#### Add Repo as Marketplace

```
/plugin marketplace add jfmario/GmToolsMarketplace
```

#### Install a Plugin

```
/plugin install pf2e-ap@gm-tools
```

### Repository Scope

Set up `.claude/settings.json` in the repository.

```json
{
    "extraKnownMarketplaces": {
        "gm-tools": {
            "source": { "source": "github", "repo": "jfmario/GmToolsMarketplace" }
        }
    },
    "enabledPlugins": {
        "pf2e-ap@gm-tools": true
    }
}
```