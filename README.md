# BTX bootstrap snapshots

Datadir snapshots of the BTX chain, taken from an independent consensus node that ExactReplays every
block itself. They exist so nobody has to wait days for a fresh node to catch up.

**Latest snapshot: [releases/latest](../../releases/latest)**

## Verify before you use it

Every release lists the archive's SHA-256 and the chain tip it was taken at.shasum -a 256 btx-datadir-<height>.tar.gz # must match the release notes tar -xzf btx-datadir-<height>.tar.gz -C /your/path btxd -datadir=/your/path/btxdata -prune=4096 btx-cli -datadir=/your/path/btxdata getblockcount btx-cli -datadir=/your/path/btxdata getbestblockhash

Then check that tip hash against at least two independent sources of your own. Do not take anyone's
word for which chain a snapshot is on, including mine.

## What these are, and are not

- **Pruned.** History starts at block 184,942. Your node will also be pruned. This is a fast way to
  become current. It is **not** an archive and it cannot serve old blocks to other people.
- If you want to run an archive or feeder node, sync unpruned instead. The network is short of those,
  and that shortage is what caused the September 2026 outage.
- **No config, no wallet.** The archive contains no `btx.conf` and no wallet files. Bring your own.
- Each snapshot reflects the chain carrying the large majority of proof of work at the moment it was
  taken. That is a measurement, not a vote.

## Cadence

Refreshed regularly while the network needs it. Older releases are left up so you can see the history.
