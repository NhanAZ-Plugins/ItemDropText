# ItemDropText

ItemDropText displays a configurable floating label above dropped item entities on an Axolotl-PM server. It updates the label when item entities merge. A label that includes `{despawnDelay}` is refreshed once per second.

## Requirements and compatibility

- Axolotl-PM plugin API `5.0.0`, as declared in [`plugin.yml`](plugin.yml).
- PHP 8.1 or newer with the Axolotl-PM 5 runtime.
- No external plugin or runtime library dependency.

PHPStan at maximum level passes against the Axolotl-PM 5.0.0 and 5.49.1 source revisions. This verifies those API surfaces, not every intermediate 5.x release. A Bedrock client is required to confirm the appearance of floating labels in game.

## Installation

Download a verified PHAR from [GitHub Releases](https://github.com/NhanAZ-Plugins/ItemDropText/releases), place it in the server's `plugins` directory, and restart Axolotl-PM.

## Configuration

Edit `plugins/ItemDropText/config.yml` after the first startup. The default format is `{name} x{count}`. The plugin supports these placeholders.

| Placeholder | Value |
| --- | --- |
| `{name}` | Custom item name, or the standard name when none is set |
| `{vanillaName}` | Standard item name |
| `{count}` | Number of items in the entity stack |
| `{attackPoints}` | Item attack points |
| `{cooldownTicks}` | Item cooldown in ticks |
| `{defensePoints}` | Item defense points |
| `{maxStackSize}` | Maximum stack size |
| `{lore}` | Item lore lines |
| `{despawnDelay}` | Remaining despawn time, refreshed once per second |

Use `&` or `§` color codes. A format value with a nonstring YAML type produces a warning and uses the default format in memory. The file is not overwritten. If you include `{despawnDelay}`, consider the cost of refreshing every loaded dropped item each second on a busy server.

## Build and verification

The [build workflow](.github/workflows/build.yml) runs PHPStan at maximum level against a pinned Axolotl-PM source revision, then uses [DevTools](https://github.com/NhanAZ/DevTools) to build and inspect the PHAR. Workflow revisions are pinned for reproducibility. The exact tested runtime revision and artifact are available from the linked workflow run.

The server startup check verifies that the PHAR enables. It does not confirm client rendering, item merge behavior or performance under a large number of dropped items.

## License and support

ItemDropText retains its [MIT license](LICENSE). Report issues through [GitHub Issues](https://github.com/NhanAZ-Plugins/ItemDropText/issues) or contact [NhanAZ Discord](https://discord.gg/j2X83ujT6c).
