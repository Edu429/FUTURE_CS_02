# Phishing Email Detection & Awareness Report
Future Interns – Cyber Security Internship, Task 2
Author: EDWIN MWONGERA. 
Github: (Edu429)

## 1. Summary
I analysed 10 emails: 6 phishing and 4 safe. The phishing set contains five credential-harvesting emails that impersonate IT teams or well-known brands, and one advance-fee scam. Every phishing email used urgency or fear, a generic greeting, and a request to click a link or hand over something sensitive. The safe set contains three ordinary mailing-list or feed messages and one legitimate marketing email whose headers pass SPF, DKIM and DMARC.

## 2. Method
1. Selected sample emails from public Kaggle datasets (Nazario phishing corpus, Nigerian Fraud, SpamAssassin) using a Python script to filter out unreadable rows.
2. Checked each email for sender or domain mismatch, urgency, threats, generic greetings, spelling and grammar errors, and requests for credentials or money.
3. Classified each email as Safe, Suspicious or Phishing.
4. Analysed the authentication headers of one real email from my own inbox.
5. Redacted personal details before publishing. No links were opened.

## 3. Findings
See the table in the README. Details per email:

**Sample 839 – Phishing (fake LinkedIn).** Display name says "LinkedIn Security" but the address uses an unrelated .cf domain; LinkedIn does not send from it. It threatens account termination, uses a generic "Dear," greeting, has a typo ("Comfirm") and asks the reader to mark it "not spam".

**Sample 1206 – Phishing (fake mail queue notice).** The display name "monkey.org" does not match the sender's domain, which belongs to an unrelated business. It claims old mailbox versions will be closed and pushes the reader to "upgrade now".

**Sample 749 – Phishing (fake help desk).** A fake "RE:" subject makes it look like a reply. It cites a "federal audit", uses broken English and a generic "Help Desk Support Team" sign-off. The sender appears to be a compromised real account.

**Sample 639 – Phishing (fake deletion request).** Claims a request was made to delete the mailbox and tells the reader to click to cancel. This creates panic so the reader acts without thinking.

**Sample 579 – Phishing (storage limit).** Claims the mailbox is full and asks the reader to "verify" the account. A leftover "(FILL)" template marker shows it was mass-produced.

**Sample 825 – Phishing (advance-fee fraud).** Claims to come from a government ministry director but uses a free webmail address. It stresses secrecy, promises millions of dollars and asks for help moving money offshore. This is a typical setup before fees or bank details are requested.

**Samples 3598, 596, 2039 – Safe.** Ordinary discussion or feed content with no credential requests, no urgency and no pressure. Sample 2039 has an odd-looking sender domain, which shows that content and behaviour matter as well as the address.

## 4. Email header analysis
| Check | Result |
|---|---|
| SPF | Pass |
| DKIM | Pass (signed by the sender's domain and by the delivery service) |
| DMARC | Pass (policy: quarantine, domain aligned) |
| Transport | TLS 1.3 |
| Bulk-mail signs | Unsubscribe headers, click tracking, open-tracking pixel |

Verdict: Safe, a legitimate marketing email. Passing authentication shows that the sender controls the domain it claims. It does not prove the sender is trustworthy, because attackers can also set up valid authentication on their own lookalike domains. For a phishing email, signs to look for are SPF or DKIM failing, DMARC failing, and a Return-Path or Reply-To that does not match the From address. The dataset emails did not include raw headers, and no suitable phishing email was found in my own inbox, so a failing example was not analysed.

## 5. Common phishing techniques
- **Spoofing and lookalike domains:** the display name says one organisation while the real address belongs to another.
- **Urgency and fear:** threats of closure, deletion or termination push people to act before thinking.
- **Credential harvesting:** a link leads to a fake login page that captures the password.
- **Impersonating IT or well-known brands:** "help desk" and "security team" messages look official.
- **Advance-fee fraud:** a huge reward is offered in exchange for help, followed by requests for fees or bank details.

## 6. Prevention guidelines
**For users**
- Check the real sender address, not just the display name.
- Don't click links or open attachments from unexpected messages; go to the website directly.
- Never share passwords or one-time codes by email.
- Treat urgency, threats and "too good to be true" offers as warning signs.
- If unsure, confirm through a separate channel, such as calling the organisation, and report it to IT.

**For organisations**
- Publish SPF, DKIM and DMARC records and move DMARC toward an enforcing policy.
- Require multi-factor authentication so stolen passwords alone are not enough.
- Run regular phishing awareness training and simple simulations.
- Make reporting easy, and quarantine suspicious email automatically.

## 7. Limitations
- The dataset emails are older and contain subject and body only, with no raw headers or live link destinations.
- Only one email had full header results.
- Sample size is small (10 emails) and chosen by me.
- A Python script skipped malformed CSV rows when loading the datasets, so the row counts are lower than the full datasets and samples were drawn from the rows that parsed correctly.

## 8. Sources
- Alam, N. A. "Phishing Email Dataset" (Kaggle): https://www.kaggle.com/datasets/naserabdullahalam/phishing-email-dataset (Nazario, Nigerian Fraud and SpamAssassin files).
