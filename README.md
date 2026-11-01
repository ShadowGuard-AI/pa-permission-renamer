# pa-permission-renamer
Simulation only: this tool renames nothing. It is a placeholder that simulates permission renaming: it walks a directory, reads each entry's real permission string, and reports which entries would be renamed under a CSV mapping file. No file, name, or permission is ever changed by any run.

## Install
`git clone https://github.com/ShadowStrikeHQ/pa-permission-renamer`

## Usage
`./pa-permission-renamer [params]`

## Parameters
- `-h`: Show help message and exit
- `-m`: Path to the CSV mapping file (old_permission,new_permission). Keys are permission strings in the nine character form, for example `rwxr-xr-x` or `rw-r-----`.
- `-d`: The root directory to simulate permission renaming over. Simulation only: nothing in this directory will be changed.
- `-v`: Enable verbose logging.

## Behaviour notes
- The simulation is computed from each entry's real mode. A file at mode 0o640 is reported with the string `rw-r-----`, a directory at mode 0o755 with `rwxr-xr-x`, and a mapping keyed on a real permission string can match.
- An empty mapping file, an empty directory, and a run in which no entry matches the mapping all end with a plain nothing was simulated message and exit non-zero. A run that simulates at least one match ends with a simulation complete line that states how many entries would change and that no permissions were renamed.

## License
Copyright (c) ShadowStrikeHQ
