# Verify this tool yourself

This overlay reads another process's memory, ships unsigned, and comes from a
pseudonymous developer. You should not take its safety claims on faith — this
page exists so you don't have to. Every claim below is checkable on your own
machine with free tools, against the exact binary you downloaded.

## Release hash history (append-only)

Every release ever published, newest first. This table is never rewritten —
if a hash you downloaded is not in this list, you did not get it from here.

| Version | Date | File | SHA-256 |
|---|---|---|---|
<!--NEXT-RELEASE-ROW-->
| v0.8.0 | 2026-08-20 | FF7RebirthGuide-v0.8.0-win64.zip | `da504e1f79e126a645f569a3f767aa93284bbc45b837ad295b713159f3dcbe1b` |
| v0.8.0 | 2026-08-20 | FF7RebirthGuide.exe | `dffe0992c8cf3aaa5ffb16b0f4a188160769c39123c34a96b5308ea8352879d1` |
| v0.7.0-rc2 | 2026-08-19 | FF7RebirthGuide-v0.7.0-rc2-win64.zip | `7217f901308793be21113b849deaedc1e12a5341f56a1ae1688cc0fa83eff048` |
| v0.7.0-rc2 | 2026-08-19 | FF7RebirthGuide.exe | `f4d4ca90e17370bf5ea35df6eeccc43f71ee5fddc687e84dc45121333a596284` |

Check your download with:

```
certutil -hashfile FF7RebirthGuide.exe SHA256
```

## Verify the claims, not the promises

**"It never touches the network."** The binary imports no networking DLLs.
With Visual Studio's `dumpbin` (or any PE viewer like PE-bear):

```
dumpbin /imports FF7RebirthGuide.exe
```

You will find no `winhttp.dll`, `wininet.dll`, `ws2_32.dll` or any other
network import. You can also watch it live: Sysinternals Process Monitor
filtered to the process shows zero TCP/UDP operations, and any outbound
firewall rule never fires. (The "Check for updates" button opens your default
BROWSER at the GitHub releases page — the overlay process itself makes no
connection.)

**"It only reads, never writes."** Run the game and the overlay, open
Sysinternals Process Explorer, find `FF7RebirthGuide.exe`, and inspect its
handle to the game process: the access mask requests read/query rights, not
`PROCESS_VM_WRITE` / `PROCESS_VM_OPERATION`. Process Monitor over a whole
session shows no writes into the game's files or memory, and no writes
anywhere outside its own folder (settings `.ini` files and a session log next
to the exe).

**"No injection, no hooks."** The game process gains no loaded module from
this tool (compare the game's module list with and without the overlay
running, e.g. in Process Explorer's DLL view). The overlay is an ordinary
external window that draws on top — nothing runs inside the game.

**Reproducible builds.** The exe is built with `/Brepro` and a pinned
toolchain: the same source produces byte-identical binaries, which is what
makes a public hash history meaningful.

## Antivirus notes

Machine-learning heuristics at a few engines flag fresh, unsigned,
low-prevalence executables that read process memory — that is this tool's
exact shape, so expect a few ML flags on VirusTotal (the release notes link
the current scan). Every release is submitted to Microsoft's false-positive
review before it is announced. If your AV quarantines the file, verify the
hash against the table above and restore/allow it — or don't run it; that is
always a legitimate choice with an unsigned tool.
