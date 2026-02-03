# n8n Mail Attachments to SharePoint V1

Automatisierter n8n Workflow: E-Mail-Anhänge aus Outlook abholen, OCR für PDFs, KI-Kategorisierung, Upload zu SharePoint.

## Was macht der Workflow?

1. Holt Mails mit Anhängen aus Outlook Posteingang
2. Filtert Inline-Bilder und Kalender-Dateien raus
3. PDFs → OCR via Stirling-PDF
4. KI analysiert Dateinamen → Kategorie (Rechnungen, Verträge, etc.)
5. Upload zu SharePoint in passenden Ordner
6. Mail verschieben (erfolgreich/fehler)

## Voraussetzungen

- n8n
- Microsoft 365 (Outlook + SharePoint)
- [Stirling-PDF](https://github.com/Stirling-Tools/Stirling-PDF) für OCR
- Anthropic API Key

## Installation

1. `workflow.json` in n8n importieren
2. Credentials einrichten (Outlook OAuth2, SharePoint OAuth2)
3. Platzhalter ersetzen (siehe unten)
4. In Outlook Ordner `n8n-erfolgreich` und `n8n-fehler` erstellen

## Platzhalter

| Platzhalter | Beschreibung |
|-------------|--------------|
| `{{OUTLOOK_INBOX_FOLDER_ID}}` | Posteingang Folder ID |
| `{{OUTLOOK_SUCCESS_FOLDER_ID}}` | Ordner für verarbeitete Mails |
| `{{OUTLOOK_ERROR_FOLDER_ID}}` | Ordner für Fehler-Mails |
| `{{OUTLOOK_CREDENTIAL_ID}}` | n8n Credential ID |
| `{{SHAREPOINT_SITE_URL}}` | z.B. `https://contoso.sharepoint.com/sites/DMS` |
| `{{SHAREPOINT_DMS_PATH}}` | z.B. `/sites/DMS/Dokumente/Mail Anhänge` |
| `{{SHAREPOINT_CREDENTIAL_ID}}` | n8n Credential ID |
| `{{STIRLING_PDF_URL}}` | z.B. `https://ocr.example.com` |
| `{{ANTHROPIC_API_KEY}}` | API Key |

Folder-IDs via Graph Explorer: `GET https://graph.microsoft.com/v1.0/me/mailFolders`

## Lizenz

MIT
