# 🕷️ Skipfish Web Vulnerability Scanner – Usage & Report

This report documents a freelance task involving the use of **Skipfish**, an open-source web vulnerability scanner. The goal was to scan websites from Kali Linux, interpret the scan results, and understand the tool’s capabilities and limitations.

---

## 📌 Objectives

- Launch and use Skipfish from Kali Linux  
- Scan a live target website using the CLI  
- Generate and interpret output reports  
- Learn how wordlists, scan depth, and output directories are managed  
- Analyze findings from the generated HTML report  

---

## 🛠️ Tools & Environment

| Tool        | Purpose                                   |
|-------------|-------------------------------------------|
| Skipfish    | Web vulnerability scanner                 |
| Kali Linux  | Host OS for running Skipfish              |
| Terminal    | Command-line usage of scanner             |
| Web Browser | Viewing the generated `index.html` report |

---

## ⚙️ Skipfish Setup & Execution

Skipfish is pre-installed in Kali. To access it:

```bash
Applications → Web Application Analysis → Skipfish
```



### 🧪 Command Used:

```bash
skipfish -o 202 http://www.google.com
```

Explanation:

* `-o 202`: Saves the output in a folder named `202`
* `http://www.google.com`: The target to be scanned

Skipfish begins crawling the site and presents a launch screen. You can:

* Press any key to start scanning immediately
* Use `Ctrl + C` to stop the scan at any time

---

## 📄 Report Viewing

Once the scan completes or is interrupted:

* Navigate to the output directory (e.g., `~/202`)
* Open `index.html` in a browser to view results

The report contains:

* Summary statistics
* Detailed scan paths
* Potential vulnerabilities
* Response headers and encoding issues

---

## 🔍 Result Interpretation

* Since Google was scanned, no critical vulnerabilities were expected
* The tool still identified warnings, encoding issues, and medium-severity alerts
* Custom scans (e.g., on internal or staging apps) would reveal more actionable results

---

## 🔐 Ethical Note

Only authorized or publicly testable domains were scanned in this project. All actions were conducted within ethical and legal guidelines for client demonstration purposes.

---

## 📄 Report

[📥 View Full PDF Report](./Skipfish.pdf)

---

## 💡 What I Learned

* Hands-on experience with a fast, CLI-based web scanner
* Importance of choosing proper scan targets and dictionary files
* How HTML-based reports help visualize vulnerabilities
* Understanding the limits of automated tools and need for manual validation

> 🔍 Skipfish is great for quick scans but should be paired with deeper manual testing for full assessments.