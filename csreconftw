# Usage

> Check out the wiki section to know which flag performs what all steps/attacks [Usage Guide](https://github.com/six2dez/reconftw/wiki/2.-Usage-Guide) :book:

## TARGET OPTIONS

| Flag | Description |
|------|-------------|
| -d | Single Target domain *(example.com)*  |
| -l | List of targets *(one per line)* |
| -m | Multiple domain target *(companyName)*  |
| -x | Exclude subdomains list *(Out Of Scope)* |
| -i | Include subdomains list *(In Scope)* |

## MODE OPTIONS

| Flag | Description |
|------|-------------|
| -r | Recon - Full recon process (without attacks like sqli,ssrf,xss,ssti,lfi etc.) |
| -s | Subdomains - Perform only subdomain enumeration, web probing, subdomain takeovers |
| -p | Passive - Perform only passive steps |
| -a | All - Perform whole recon and all active attacks |
| -w | Web - Perform only vulnerability checks/attacks on particular target |
| -n | OSINT - Performs an OSINT scan (no subdomain enumeration and attacks) |
| -c | Custom - Launches specific function against target |
| -h | Help - Show this help menu |

## GENERAL OPTIONS

| Flag | Description |
|------|-------------|
| --deep | Deep scan (Enable some slow options for deeper scan, *vps intended mode*) |
| -f | Custom config file path |
| -o | Output directory |
| -v | Axiom distributed VPS |
| -q | Rate limit in requests per second |

## Example Usage

**NOTE: this is applicable when you've installed reconFTW on the host (e.g. VM/VPS/cloud) and not in a Docker container.**

### To perform a full recon on single target

```bash
./reconftw.sh -d target.com -r
```

### To perform a full recon on a list of targets

```bash
./reconftw.sh -l sites.txt -r -o /output/directory/
```

### Perform full recon with more time intense tasks *(VPS intended only)*

```bash
./reconftw.sh -d target.com -r --deep -o /output/directory/
```

### Perform recon in a multi domain target

```bash
./reconftw.sh -m company -l domains_list.txt -r
```

### Perform recon with axiom integration

```bash
./reconftw.sh -d target.com -r -v
```

### Perform all steps (whole recon + all attacks) a.k.a. YOLO mode

```bash
./reconftw.sh -d target.com -a
```

### Show help section

```bash
./reconftw.sh -h
```
