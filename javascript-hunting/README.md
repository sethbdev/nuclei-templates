# JavaScript Hunting Nuclei Suite

This suite provides a comprehensive workflow to discover, filter, analyze, and extract intelligence from JavaScript (`.js`) files on web targets. It's designed for bug bounty hunters, penetration testers, and security researchers looking to automate deep JS recon and identify hidden attack surfaces.

---

## 📁 Directory Structure

```
js-hunting/
├── js-enumeration-depth0-9.yaml
├── js-cdn-filtering.yaml
├── js-hash-files.yaml
├── js-status200-check.yaml
├── js-secret-scanning.yaml
├── js-linkfinder-gf.yaml
├── js-linkfinder-headless.yaml
├── js-hunting-workflow.yaml
└── README.md
```

---

| Template                        | Purpose                                                                 |
|---------------------------------|-------------------------------------------------------------------------|
| `js-enumeration-depth0-9.yaml` | Crawls and extracts all `.js` files from target (depth 0–9).            |
| `js-cdn-filtering.yaml`        | Filters out JS files hosted on known CDNs to reduce noise.              |
| `js-hash-files.yaml`           | Downloads each JS file and computes a SHA-256 hash for fingerprinting.  |
| `js-status200-check.yaml`      | Verifies if the JS files are accessible (`HTTP 200`).                   |
| `js-secret-scanning.yaml`      | Scans JS files for secrets (API keys, tokens, passwords, etc.).         |
| `js-linkfinder-gf.yaml`        | Uses GF-style regex patterns to identify interesting links/endpoints.   |
| `js-linkfinder-headless.yaml`  | Uses headless browser mode to extract dynamic JS references.            |
| `js-hunting-workflow.yaml`     | Chains all above templates into a single automated workflow.            |

---

## 🧠 Use Cases

- Discover hidden endpoints and internal APIs from exposed JS
- Identify secrets and sensitive keys embedded in client-side code
- Bypass traditional CDN-hosted JS by filtering it out
- Chain link-finding tools and JS URL extraction
- Track JS changes across environments with hashing

---

## 🚀 Usage

### Run against a single URL or list:

```bash
nuclei -w js-hunting/js-hunting-workflow.yaml -u <url> -json -o js-hunting-results.json
```
For List:

```bash
nuclei -w js-hunting/js-hunting-workflow.yaml -l urls.txt -json -o js-hunting-results.json

```

## 🔍 Output
JSON format: Results are saved in js-hunting-results.json

Includes: JS paths, status, SHA-256 hashes, potential secrets, interesting endpoints

##✅ Best Practices
Run this during recon to get an early idea of exposed JS surfaces

Periodically hash JS to detect changes across deployments

Use in combination with tools like `gf`, `subjs`, or `LinkFinder` for chaining

## 📬 Contributions
Feel free to submit issues, PRs, or enhancements. This suite will grow as new JS bugs, patterns, and detection techniques emerge.

## 🏴‍☠️ Disclaimer
For educational and professional use only. Do not scan systems without proper authorization.


