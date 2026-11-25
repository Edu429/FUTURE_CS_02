# Phishing Email Detection & Awareness Report
Future Interns – Cyber Security Internship (Task 2)

**Author:** EDWIN MWONGERA (Edu429)

## Objective
Analyse a set of sample emails, identify phishing indicators, classify each as Safe / Suspicious / Phishing, and provide prevention guidelines in plain business language.

## Tools Used
- Email header analyser (Google Messageheader / MXToolbox)
- VirusTotal / urlscan.io (URL checks, no direct visits)
- Browser tools
- Google Docs / PDF for the report

## Methodology
1. Collected sample emails (public datasets and redacted real examples)
2. Inspected sender, headers, links and content
3. Classified each email and documented the indicators

## Findings Summary
| # | Sample | Verdict | Key indicators |
|---|--------|---------|----------------|
| 1 | phishing_839 (fake LinkedIn) | Phishing | Wrong domain (.cf), brand impersonation, termination threat, typo, generic greeting |
| 2 | phishing_1206 (fake mail queue) | Phishing | Display name does not match sender domain, deadline pressure, auto-generated tone |
| 3 | phishing_749 (fake help desk) | Phishing | Fake "RE:" reply, "federal audit" pressure, broken English, likely compromised account |
| 4 | phishing_639 (fake deletion) | Phishing | Fake mailbox-deletion request to cause panic, generic domain |
| 5 | phishing_579 (storage limit) | Phishing | Storage-limit scam, "(FILL)" template leftover, likely compromised account |
| 6 | phishing_advancefee_825 | Phishing (advance-fee) | Official title but free webmail, "strictly confidential", multi-million offer |
| 7 | safe_3598 | Safe | Mailing-list conversation, no requests, no pressure |
| 8 | safe_596 | Safe | Discussion reply, no links or requests |
| 9 | safe_2039 | Safe | RSS blog summary, harmless content despite an odd sender domain |
| 10 | safe_kompozy | Safe | SPF, DKIM and DMARC all pass, normal marketing headers |

## Prevention Guidelines
See the full list of user and organisation guidelines in the report: [Phishing_Report.md](report/Phishing_Report.md)

## Full Report
[Phishing_Report.md](report/Phishing_Report.md)
[Phishing_Report.pdf](report/Phishing_Report.pdf)
