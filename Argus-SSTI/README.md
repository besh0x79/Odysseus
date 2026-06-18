<p align="center">
  <img src="https://i.ibb.co/S4j4dHh9/photo-5879531012860088241-y.jpg" alt="Argus Logo" width="400">
</p>


# Argus-SSTI

A lightweight SSTI (Server-Side Template Injection) engine identifier written in Python.

Argus-SSTI helps security researchers and CTF players quickly determine which template engine is being used by a vulnerable application by sending a set of fingerprinting payloads and analyzing the responses.

## Features

* Detects common SSTI template engines
* Fast and lightweight
* Useful for CTFs and penetration testing labs
* Simple payload-based fingerprinting
* No external dependencies except `requests`

## Supported Detection

| Engine         | Detection Method               |
| -------------- | ------------------------------ |
| Jinja2         | Expression evaluation          |
| Twig           | Expression evaluation          |
| Smarty         | Payload filtering behavior     |
| Mako           | Python expression behavior     |
| Unknown        | Engine could not be identified |
| Not Vulnerable | No SSTI behavior detected      |

## Installation

```bash
git clone https://github.com/besh0x79/Odysseus.git
cd Argus-SSTI
pip install requests
```

## Usage

Edit the target URL:

```python
url = "http://target.com"
```

Run:

```bash
python argus.py
```

Example output:

```text
Jinja2 or Twig
```

```text
Smarty
```

```text
Mako
```

```text
Not vulnerable
```

## How It Works

Argus-SSTI sends a series of carefully selected SSTI fingerprint payloads:

```python
${7*7}
a{*comment*}b
${"z".join("ab")}
{{7*7}}
{{7*'7'}}
```

The tool then compares the server responses against the original payloads to determine whether the payload was evaluated, filtered, or reflected back unchanged.

## Disclaimer

This tool is intended for:

* Security research
* Educational purposes
* CTF challenges
* Authorized penetration testing

Do not use this tool against systems without proper authorization.

