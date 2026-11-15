# Connections for review, fix and commit

None of these is required, and none is installed for you: a command is shown, and you run it.

| tool | what it adds | cost | tried here |
|---|---|---|---|
| a language server, through `atlas-mem` | references resolved by type rather than by text | `typescript-language-server` or `pyright` to install | yes, on JavaScript and Python |
| your CI's logs, through `gh` | `atlas fix` reads the failure as CI saw it | `gh` logged in | not run |

# Connections for atlas-code

None of these is required, and none is installed for you: a command is shown, and you run it. Each MCP server adds its tool definitions to every chat where it is on. "Tried" means it was run here, and what the test covered.

| tool | what it adds | advantages | disadvantages | tried here |
|---|---|---|---|---|
| [Context7](https://github.com/upstash/context7) | library docs for the right version | one call where a search takes four | its index decides what you get; your query leaves the machine | used through `atlas-research`, not measured |
| Chrome DevTools MCP | pages behind a login, performance traces | sees what a logged-in person sees | drives your browser and your sessions, so a page can try to instruct it | used in sessions, not measured |
| Codex CLI, through `atlas multi` | a second model's review | a reader that did not write the code | the code you show it leaves the machine, and it costs that service's usage | one real call |
| `semgrep`, `gitleaks`, `osv-scanner`, through `atlas secure` | scanners beside the reading | finds what reading misses | to install; missing ones are reported as not run, never as clean | only with the scanners missing: they were reported as not run |
| GitHub, Jira or Linear, through `atlas track` | tickets read and updated | the ticket stays the source | needs a login, and an update is visible to your team, so it asks first | not run |

# Connections for atlas-mem

None of these is required, and none is installed for you: a command is shown, and you run it. "Tried" means it was run here, and what the test covered.

| tool | what it adds | advantages | disadvantages | tried here |
|---|---|---|---|---|
| `@huggingface/transformers` | search of the notes by meaning | on 30 questions the right note came first 26 times, against 23 by words alone; stays on your machine | an npm package and a 130 MB model | yes |
| `typescript-language-server`, `pyright` | live references | types and imports resolved: 104 references where the static graph counted 53 callers on one Python symbol | to install, and 20 s on a 200-file project | yes |
| Obsidian or any Markdown editor | reading and editing the vault | the notes are plain files, so nothing is locked in | no check runs in there: run `memcheck` after editing | not as an integration |
| a claude.ai export, through `harvest docs` | past conversations as candidates | only you accept what enters the memory | calls a model, which spends your usage | yes |

# Connections for atlas-video

None of these is required, and none is installed for you: a command is shown, and you run it. "Tried" means it was run here, and what the test covered.

## Generate video from a prompt

### WanGP

Local generation of video from text or images, with models such as Wan and LTX. Good when you want no upload and no per-video fee, and you have a GPU.

- **Connect:** install it apart from this plugin, then add its own MCP server: `python wgp.py --mcp`.
- **Advantages:** runs on your machine, nothing leaves it, no fee per video. It has twelve tools for generating, listing models and post-processing.
- **Disadvantages:** models of many GB and a GPU. Every chat with the server on pays for its tool definitions. Its licence is a community licence, not an open-source one: read it, especially before any paid use.
- **Tried:** the server starts and lists its twelve tools. No video has been generated through it here.

### Any other generator

If it offers an MCP server or a command line, `atlas media` can use it when you name it. Before you connect a hosted one, check three things: what each video costs, whether your prompts and files leave your machine, and what its terms say about using the output.

## Make video from code

`atlas media` looks for these by itself. Install the one you want.

| tool | best for | watch out for | tried here |
|---|---|---|---|
| [HyperFrames](https://github.com/heygen-com/hyperframes) | HTML compositions written by an agent | its own CLI and skills to install | yes, one 47-second short; the result was not judged final |
| [Remotion](https://github.com/remotion-dev/remotion) | video written in React | its own licence: companies above a size must pay, so read it | not on a real project |
| [Manim](https://github.com/ManimCommunity/manim) | mathematical animation | a Python and LaTeX setup | not on a real project |
| Blender | checking a 3D scene by numbers | a large install | not on a real project |
