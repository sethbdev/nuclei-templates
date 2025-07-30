# Open Redirect Hunting Suite

A comprehensive Nuclei-based detection suite for open redirect vulnerabilities and chaining potential (e.g., SSRF, CSP bypass).

## File Structure

```bash
open-redirect-hunting/
├── open-redirect-detect.yaml # Core detection template
├── open-redirect-params-subtemplate.yaml # Param-based subtemplate
├── open-redirect-paths-subtemplate.yaml # Path-based subtemplate
├── helpers/
│ ├── redirect-params.txt # Common vulnerable params
│ └── redirect-paths.txt # Known redirect-prone paths
├── workflows/
│ └── open-redirect-chain.yaml # Chains detection w/ SSRF, CSP, GraphQL
└── README.md
```

## Features

- Over 100 real-world redirect vectors
- Clusterbomb fuzzing on params
- CDN-aware and domain-specific path filtering
- Workflow chaining with SSRF, CSP, and GraphQL introspection
- Easily extendable with additional payloads

## Usage

```bash
nuclei -w open-redirect-hunting/workflows/open-redirect-chain.yaml -target https://example.com
```

For educational use only. Only use on authorized systems.
