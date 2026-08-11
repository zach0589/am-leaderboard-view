# AM Leaderboard (encrypted view)

This repository serves one file: a passphrase-protected copy of the Spot On
Solutions Account Manager dashboard.

The page contains **no readable data**. The dashboard payload is encrypted with
AES-256-GCM using a key derived from a passphrase via PBKDF2-SHA256 (600,000
iterations). Decryption happens in the browser after the passphrase is entered;
nothing is transmitted anywhere. Without the passphrase the file is meaningless
bytes, which is why it is safe to host publicly.

Source code for the tool that generates this lives in a separate private
repository. Nothing here reveals how any account or person is scored.

Regenerate and publish an update:

    ./refresh.sh                    # pull fresh HubSpot data
    python3 build_secure.py --passphrase "existing-passphrase" --out public/index.html
    # then commit the new index.html to this repo

Reusing the same passphrase keeps every link and instruction you have already
sent valid.
