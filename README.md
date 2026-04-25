<h1 align="center">
  <br>
    🚀 The Company Voyage — Server
  <br>
</h1>

<h4 align="center">Dedicated Minecraft server for <strong>The Company Voyage</strong> — a space pirate adventure built on <a href="https://neoforged.net/" target="_blank">NeoForge 1.21.1</a> with custom cubic planets, space dimension, static fluids and pirate-themed gameplay.</h4>

<p align="center">
  <a href="#mods">Mods</a> •
  <a href="#requirements">Requirements</a> •
  <a href="#how-to-run">How to Run</a> •
  <a href="#deploy">Deploy</a> •
  <a href="#client-setup">Client Setup</a> •
  <a href="#configuration">Configuration</a> •
  <a href="#author">Author</a>
</p>

---

## Mods

### Custom

| Mod                                                                   | Description                                                                       |
| --------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| [cleyde_espacial](https://github.com/niloodev/the_company_voyage_mod) | Core mod — space dimension, cubic planets, static fluids, biome music, custom sky |

### World Generation

| Mod                                                                          | Version |
| ---------------------------------------------------------------------------- | ------- |
| [Oh The Biomes We've Gone](https://modrinth.com/mod/oh-the-biomes-weve-gone) | 2.5.5   |
| [Oh The Trees You'll Grow](https://modrinth.com/mod/oh-the-trees-youll-grow) | 5.3.0   |
| [TerraBlender](https://modrinth.com/mod/terrablender)                        | 4.1.0.8 |

> **BWG is required by `cleyde_espacial`** — the space dimension biome list references BWG biomes. Without it the server will not start.

### Mobs & Creatures

| Mod                                                                         | Version |
| --------------------------------------------------------------------------- | ------- |
| [Creeper Overhaul](https://modrinth.com/mod/creeper-overhaul)               | 4.0.6   |
| [Enderman Overhaul](https://modrinth.com/mod/enderman-overhaul)             | 2.0.3   |
| [Golem Overhaul](https://modrinth.com/mod/golem-overhaul)                   | 1.1.0   |
| [Ribbits](https://modrinth.com/mod/ribbits)                                 | 4.1.6   |
| [Companions](https://modrinth.com/mod/companions)                           | 1.2.2   |
| [Critters and Companions](https://modrinth.com/mod/critters-and-companions) | 2.3.4   |
| [Corgilib](https://modrinth.com/mod/corgilib)                               | 5.0.0.9 |

### Gameplay

| Mod                                                                                  | Version |
| ------------------------------------------------------------------------------------ | ------- |
| [Create](https://modrinth.com/mod/create)                                            | 6.0.9   |
| [Create Aeronautics](https://modrinth.com/mod/create-aeronautics)                    | 1.0.2   |
| [Rustic Engineer](https://modrinth.com/mod/rustic-engineer)                          | 1.1.4   |
| [Meteor Shower](https://modrinth.com/mod/meteor-shower)                              | 0.0.4   |
| [Explosive Enhancement](https://modrinth.com/mod/explosive-enhancement)              | 1.1.2   |
| [Night Lights](https://modrinth.com/mod/night-lights)                                | 1.3.0   |
| [Sable](https://modrinth.com/mod/sable)                                              | 1.0.6   |
| [Custom NPCs (Unofficial)](https://www.curseforge.com/minecraft/mc-mods/custom-npcs) | 1.21.1  |
| [Field Guide](https://modrinth.com/mod/field-guide)                                  | 1.6.9   |
| [World Edit](https://modrinth.com/mod/worldedit)                                     | 7.3.8   |

### Performance & Utility

| Mod                                                           | Version     |
| ------------------------------------------------------------- | ----------- |
| [Distant Horizons](https://modrinth.com/mod/distanthorizons)  | 3.0.1-b     |
| [Lithium](https://modrinth.com/mod/lithium)                   | 0.15.3      |
| [Chunky](https://modrinth.com/mod/chunky)                     | 1.4.23      |
| [JEI](https://modrinth.com/mod/jei)                           | 19.27.0.340 |
| [Travelers Titles](https://modrinth.com/mod/travelers-titles) | 5.1.3       |

### Libraries

| Mod                | Version |
| ------------------ | ------- |
| Architectury       | 13.0.8  |
| GeckoLib           | 4.8.4   |
| KnightLib          | 1.3.0   |
| OctoLib            | 0.6.1   |
| Resourceful Config | 3.0.11  |
| Resourceful Lib    | 3.0.12  |
| YUNG's API         | 5.1.6   |

---

## Requirements

| Dependency   | Version          |
| ------------ | ---------------- |
| Java         | 21               |
| Minecraft    | 1.21.1           |
| NeoForge     | 21.1.219         |
| RAM (server) | 6 GB recommended |

---

## How to Run

### Linux / WSL

```bash
./run.sh
```

### Windows

```bat
run.bat
```

The server starts on port `25565` by default. Edit `server.properties` to change it.

### JVM flags

Already configured in `user_jvm_args.txt`:

```
-Xmx6G
-Xms2G
-XX:+UseZGC
-XX:+ZGenerational
```

ZGC is required for Distant Horizons — G1GC causes performance warnings with DH's LOD generation.

---

## Deploy

After building [`cleyde_espacial`](https://github.com/niloodev/the_company_voyage_mod), deploy the mod and reset the space dimension cache:

```bash
# 1. Copy new mod jar
cp /path/to/cleyde_espacial_mod/build/libs/cleyde_espacial-1.0.0.jar mods/

# 2. Delete cached space dimension (required after any worldgen change)
rm -rf world/dimensions/cleyde_espacial/space/
```

> Always delete the dimension folder after changes to `ChunkGenerator`, `BiomeSource`, biome list or dimension JSON. Old chunks are not regenerated otherwise.

---

## Client Setup

Players need the following on their client:

### 1. Mods (same as server)

Install all mods from the [Mods](#mods) section into the client `mods/` folder. The client also needs:

| Client-only mod                                              | Purpose                   |
| ------------------------------------------------------------ | ------------------------- |
| [Oculus](https://modrinth.com/mod/oculus)                    | Shader support (optional) |
| [Distant Horizons](https://modrinth.com/mod/distanthorizons) | Extended render distance  |

### 2. Resource pack — `cleyde_titles`

Must be installed and **enabled** in Options → Resource Packs.

Provides:

- Custom music for `space_void` and `empty_sea` biomes (`.ogg` files)
- Dimension entry title: **"Espaço Sideral"**
- Biome name: **"Vazio Abissal"** for `empty_sea`

### 3. Travelers Titles config

In `config/travelerstitles-neoforge-1_21.toml`, set:

```toml
"Only Show Biome Titles When Exposed To Skylight" = false
```

### 4. JVM args (Distant Horizons)

Set in your launcher (CurseForge → instance → Java settings → Additional JVM Args):

```
-XX:+UseZGC -XX:+ZGenerational
```

### Distant Horizons cache

After a server-side worldgen update, delete the DH cache on the client to avoid stale LOD data:

```
# Windows (CurseForge)
%AppData%\CurseForge\minecraft\Instances\Cleyde Espacial\Distant_Horizons_server_data\
```

---

## Configuration

Key files:

| File                | Purpose                                 |
| ------------------- | --------------------------------------- |
| `server.properties` | Port, gamemode, difficulty, max players |
| `user_jvm_args.txt` | JVM heap and GC flags                   |
| `ops.json`          | Operator list                           |
| `whitelist.json`    | Whitelist (if enabled)                  |
| `config/`           | Per-mod configuration                   |

---

## Author

**made by niloodev | Ezequiel Nilo**

**ANY TIPS OR FEEDBACK IS HIGHLY APPRECIATED!**
