# Install rsync on ESXi

I found myself wanting to backup an ESXi VM, but it turns out ESXi doesn't include rsync. Fortunately there's a statically compiled version that you can SCP over.

I used the following rsync command and got 100Mbps+ transfer speeds:
` nohup rsync --exclude file_or_dir_to_exclude -rltv --progress --human-readable --delete -e 'ssh -T -c aes128-gcm@openssh.com -o Compression=no -x' --rsync-path=/tmp/rsync-static <source> <destination>`

Note: Binary worked on ESXi 6.7

Source: https://damiendebin.net/blog/2013/12/06/esxi-5-dot-1-and-rsync/