# SCP files quickly on a LAN

From a Mac to another system:
`rsync --exclude file_or_dir_to_exclude -rltv --progress --human-readable -e 'ssh -T -c aes128-gcm@openssh.com -o Compression=no -x' source destination:/path/to/folder --dry-run`

Source: https://gist.github.com/KartikTalwar/4393116
