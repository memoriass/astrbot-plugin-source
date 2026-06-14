# memoriass AstrBot Plugin Source

Personal AstrBot plugin registry generated from public GitHub repositories under `memoriass`.

## Source URL

After this repository is pushed to GitHub, add this URL in AstrBot WebUI:

```text
https://raw.githubusercontent.com/memoriass/astrbot-plugin-source/main/plugins.json
```

AstrBot will automatically look for the matching MD5 file at:

```text
https://raw.githubusercontent.com/memoriass/astrbot-plugin-source/main/plugins-md5.json
```

## Update

Regenerate the registry:

```powershell
python scripts/build_registry.py
```

Then commit and push:

```powershell
git add plugins.json plugins-md5.json README.md scripts/build_registry.py
git commit -m "Update plugin registry"
git push
```

## Included Repositories

The generator includes public repositories that expose a root-level `metadata.yaml` compatible with AstrBot plugins.

