# Casdoor

## Repository

| Remote   | URL                                 |
| -------- | ----------------------------------- |
| origin   | git@github.com:sususu98/casdoor.git |
| upstream | git@github.com:casdoor/casdoor.git  |

## Dependencies

```
sususu98/casdoor
    └── sususu98/ldapserver
            └── sususu98/goldap (ASN.1 encoding fix)
```

## Local Workspace

```
~/workspace/
├── casdoor/      origin: sususu98/casdoor     upstream: casdoor/casdoor
├── ldapserver/   origin: sususu98/ldapserver  upstream: casdoor/ldapserver
└── goldap/       origin: sususu98/goldap      upstream: lor00x/goldap
```

## Fix

- **goldap**: Fixed `sizeInt64`/`writeInt64` for message ID >= 128
- Resolves LDAP auth failures (e.g., Jellyfin) on long connections
## Common Commands

```bash
# Sync upstream updates
git fetch upstream
git merge upstream/master

# Update dependency chain (goldap → ldapserver → casdoor)
cd ~/workspace/goldap && git push
cd ~/workspace/ldapserver && go get github.com/sususu98/goldap@latest && git push
cd ~/workspace/casdoor && go get github.com/sususu98/ldapserver@latest && go mod tidy
```
