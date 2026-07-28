# Day 04 – Storage II (Files, AzCopy)

**Exam domain:** Storage
**Date completed:** 07/26/2026

## What I built
Created a Standard-performance storage account and a classic (SMB) file share, deliberately
avoiding Azure's newer `Microsoft.FileShares` resource type, which only supports NFS.
Attempted to mount the share locally using the portal's generated Connect script, which
tests port 445 connectivity before mounting. Installed AzCopy and used it with a
container-scoped SAS token to transfer a local file directly into Blob Storage over HTTPS,
without ever using the storage account key.

## Key commands / concepts used
winget install Microsoft.AzCopy
azcopy --version
azcopy copy "<local-file-path>" "<destination-blob-SAS-URL>"

## Troubleshooting log
1. **`Microsoft.FileShares` NFS trap:** searching "file shares" in the portal search bar
   surfaced Azure's newer standalone file share resource type, which only supports NFS and
   never creates a storage account. Diagnosed via "Storage accounts: 0" in the Storage
   center overview. Fixed by recreating deliberately through Storage accounts → Classic
   file shares.
2. **AzCopy not installed:** `azcopy --version` returned "term not recognized." Installed
   via `winget install Microsoft.AzCopy` — the same terminal window still couldn't find the
   command afterward, since only newly opened terminals pick up the updated PATH.
3. **PowerShell argument quoting:** early `azcopy copy` attempts failed from a missing space
   between arguments and an unquoted `&` inside the SAS URL. Wrapping the destination URL in
   its own quotes fixed both.
4. **SMB blocked on port 445:** the Connect script's connectivity pre-check failed with
   `DestinationHostUnreachable` — my home ISP blocks outbound SMB by default. Confirmed
   independently with `Test-NetConnection`. Worked around it via AzCopy, which uses HTTPS
   (443) instead of SMB.
5. **"Primary service" storage account trap:** selecting "Azure Files" as the Primary
   service during storage account creation produces a `FileStorage`-kind account that only
   supports file shares — no Containers blade at all. Had to create a second
   general-purpose storage account with "Azure Blob Storage" selected as Primary service to
   get Containers for the AzCopy step.

## What I learned / what surprised me
Azure's newer `Microsoft.FileShares` resource type only supports NFS and skips creating a
storage account entirely — the correct path for SMB is Standard storage account → Classic
file shares. My home network blocks SMB outbound, which is common and unrelated to Azure
configuration. AzCopy sidesteps this by authenticating over HTTPS with a SAS token instead
of mounting a share, so the transfer succeeded even without a mounted drive. A storage
account's "Primary service" selection isn't just guidance — it actually restricts which
data services (blob vs. file) are available afterward.

## Screenshots
![Resource group + storage account created](screenshots/01-storage-account-standard.png)
![Classic (SMB) file share created](screenshots/02-classic-file-share-smb.png)
![SMB connectivity test](screenshots/03-smb-connection-test.png)
![AzCopy installation](screenshots/04-azcopy-installed.png)
![Container, SAS, and file transfer](screenshots/05-azcopy-transfer-completed.png)