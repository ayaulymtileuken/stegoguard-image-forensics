# Lesson 3 · StegoGuard Image Forensics with GitHub Actions

## Project Overview
StegoGuard is a Python-based security scanner aimed to detect suspicious hidden data inside image files. 

## How the lab works

`lab_mode.txt` controls which image `make_demo_image.py` generates. In `clean` mode the image ends at the `IEND` chunk. In `suspicious` mode the generator adds harmless demo text after that chunk. Each workflow run generates a fresh `images/student_image.png` and runs `scanner.py`.

The scanner checks the file signature and looks for the expected ending marker, trailing data, and configured keywords. It searches file bytes for keywords without regard to ASCII letter case. These are basic checks. A keyword can occur in legitimate content, and a passing scan means the configured checks found no issue in the file that was scanned. Use the generated demo image and harmless text throughout the lab.

| Repository path | Purpose |
| --- | --- |
| `lab_mode.txt` | Selects `clean` or `suspicious` mode |
| `make_demo_image.py` | Generates the demo PNG |
| `scanner.py` | Scans the image and reports each finding |
| `images/` | Holds the generated image in the workflow |
| `.github/workflows/stegoguard.yml` | Defines when and how GitHub Actions runs the lab |

## Detection Rules
StegoGuard currently checks for the following suspicious keywords:
- hidden_message
- secret
- password
- token
- api_key
- confidential
- malware
