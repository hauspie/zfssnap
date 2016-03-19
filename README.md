# ZFS Snap

`zfsnap` is a tool to automate zfs snapshot and is supposed to be run
in a cron job.

# Author

Michaël Hauspie <http://cristal.univ-lille.fr/~hauspie>

# Configuration Variables.

You should use `/etc/zfssnaprc` or `$HOME/.zfssnaprc` to change the
values, not edit the script.

    SNAP_KEPT_COUNT=3

How many snapshot should be kept.  Older snapshots will be deleted
so that `$SNAP_KEP_COUNT` snapshots left **AFTER** executing the current
snapshot.

    SNAP_DATASET="rpool"

The name of the dataset to snap.

    SNAP_RECURSIVE="yes"

Should the snapshot be recursive (-r option of zfs utility). The
script test for `yes` value. Any other value will result in non
recursive snapshot

    SNAP_PREFIX="auto-"

A prefix prepended to your snapshot. The suffix will be the date using
`YY-MM-DD-HH:MM:SS` format

    SNAP_ZFS_CMD="/usr/bin/zfs"

The zfs command to use. Useful if you need `sudo` or if the `zfs`
command is not in your `PATH` environment variable.

# Cron setup

The easiest way to set the cron job is to put this script in
`/etc/cron.hourly` to get snapshots every hour. You can of course use
a cron script in `/etc/cron.d` or any `crontab` to get more control.
