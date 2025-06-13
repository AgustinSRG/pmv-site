---
title: Making backups
description: >
  Make backups of your vault, to prevent any data losses.
categories: [Tutorials]
tags: [tutorials]
weight: 8
---

In order to make backups of your vault, you can just make regular copies of the vault folder. Due to its design, it's always in a consistent status and spreads the data into multiple files, so any external backup tool will work.

Here is the list of alternatives you can use:

 - Using the specific tool provided By PersonalMediaVault.
 - Using an standard tool, like [rsync](https://linux.die.net/man/1/rsync).
 - Using any other external tool, for example the ones provided by the main cloud storage providers.

In this tutorial we'll explain how to use the backup tool provided by the PersonalMediaVault installation.

## Using the backup tool from the launcher

When opening a vault from the launcher, you get a CLI interface with multiple commands.

In order to make a backup, use the `backup` command:

```sh
backup /path/to/backup/folder
```

In case the destination path is not empty, it will only copy the new files and update the ones that have been modified.

## Using the backup tool from the terminal

You can also use the backup tool from the terminal, running the `pmv-backup` binary:

```sh
pmv-backup backup /path/to/vault /path/to/backup/folder
```

## Re-encrypting

In case you got the encryption key leaked, and it's no longer secure, you can make a backup re-encrypting everything with a brand new randomly generated encryption key. 

In order to do that, use the `re-encrypt` option:

```sh
pmv-backup re-encrypt /path/to/vault /path/to/backup/folder
```

Note: The re-encryption process may take a very long time. Make sure to always use a secure password in order to prevent data leaks in the first place.

## Key recovery

Since restoring backup can take a long time, you may want a method to recover access to your vaulty fast in case you lose access to your credentials.

You can use the `key-export` option of the backup tool in order to export the vault encryption key:

```sh
pmv-backup key-export /path/to/vault
```

Make sure to back it up in a secure and private place.

In case you lose access to your vault, and want to recover the key, you can use the `key-recover` option of the backup tool:

```sh
pmv-backup key-recover /path/to/vault
```
