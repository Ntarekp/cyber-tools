# CyberTools

CyberTools is a collection of offensive-security and OSINT resources. The repository combines a static security cheatsheet website with small Python utilities for common reconnaissance and password-auditing workflows.

## Contents

### Offensive Security Cheatsheet

The `cheatsheet.github.io/` directory contains the generated static site for the **Offensive Security Cheatsheet**. It includes notes and commands covering topics such as:

- Linux and Windows systems
- Network and service enumeration
- Web attacks and web penetration testing
- OSINT and reconnaissance
- Cryptography
- Password cracking and hash files
- Wireless security
- Defensive monitoring and CTI
- Cloud, containers, Kubernetes, and other systems

The site is plain HTML, CSS, and JavaScript and can be opened locally or served by any static web server.

When changes are pushed to the `main` branch, the included GitHub Actions workflow publishes this directory to GitHub Pages. For this repository, the default project URL is:

<https://ntarekp.github.io/cyber-tools/>

### WaybackPDF

`WaybackPDF/` contains a Python utility that queries the Internet Archive's Wayback Machine and downloads archived PDF files for a domain.

See [WaybackPDF/README.md](WaybackPDF/README.md) for the complete command reference.

### Wrapcat

`Wrapcat/` contains a Python wrapper around Hashcat. It runs configurable wordlist, rule, mask, and charset attacks, and can also inspect or save cracked results.

See [Wrapcat/README.md](Wrapcat/README.md) for configuration, modes, examples, and benchmark information.

## Requirements

- A modern web browser for the cheatsheet
- Python 3 for the utilities
- The `requests` package for `WaybackPDF`
- Hashcat, compatible wordlists, rules, and charsets for `Wrapcat`

The utilities are independent of the website and can be used separately.

## Getting Started

### View the cheatsheet locally

Open `cheatsheet.github.io/index.html` in a browser, or serve the directory with a local static server:

```bash
cd cheatsheet.github.io
python3 -m http.server 8000
```

Then visit <http://localhost:8000>.

### Enable GitHub Pages

1. Push the repository to GitHub, including `.github/workflows/pages.yml`.
2. Open the repository's **Settings > Pages** page.
3. Set the source to **GitHub Actions**.
4. Push to `main`, or start **Deploy cheatsheet to GitHub Pages** manually from the **Actions** tab.

The workflow publishes only `cheatsheet.github.io/`; the Python utilities remain local command-line applications.

### Run WaybackPDF

Install its dependency and display the command help:

```bash
cd WaybackPDF
python3 -m pip install requests
python3 waybackPDF.py --help
```

Example:

```bash
python3 waybackPDF.py --domain example.com --output example-pdfs
```

### Configure and run Wrapcat

Before running `Wrapcat`, update the paths near the top of `Wrapcat/wrapcat.py` so they point to the local Hashcat installation, wordlists, rules, and charsets. Then inspect the available options:

```bash
cd Wrapcat
python3 wrapcat.py --help
```

Example for an authorized NTLM password audit:

```bash
python3 wrapcat.py --hashtype 1000 --hashfile HASH_FILE.txt --potfile POT_FILE.txt
```

## Repository Layout

```text
.
├── cheatsheet.github.io/   Static Offensive Security Cheatsheet
├── WaybackPDF/             Wayback Machine PDF downloader
├── Wrapcat/                Hashcat wrapper
└── README.md               Project documentation
```

## Responsible Use

Use these materials only on systems, accounts, domains, and data that you own or have explicit permission to assess. Respect the terms of service and access policies of external services, including the Internet Archive. The authors are not responsible for misuse or damage resulting from these tools or notes.

## Status

The cheatsheet is a collection of practical reference material, while the Python utilities are small, configurable scripts. Review each tool's local README and source before using it in a new environment; paths, dependencies, APIs, and command behavior may need adjustment.
