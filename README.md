[README.md](https://github.com/user-attachments/files/33131890/README.md)
# Translation Review Instrument: setup

Two files:

- **index.html**: the review form reviewers open. It goes on GitHub Pages.
- **Code.gs**: a small Google Apps Script that saves each submitted review into a Google Sheet you own.

Setup takes about 15 minutes, and you only do it once.

## 1. Create the results sheet (Google)

1. Go to sheets.google.com and create a blank spreadsheet. Name it something like *Translation Review – Results*.
2. In the menu, choose **Extensions → Apps Script**.
3. Delete the sample code in the editor, paste in everything from **Code.gs**, and click **Save** (the disk icon).
4. Click **Deploy → New deployment**.
   - Click the gear next to "Select type" and choose **Web app**.
   - **Execute as:** Me
   - **Who has access:** Anyone
   - Click **Deploy**, then **Authorize access**. Choose your Google account. If Google says the app isn't verified, click **Advanced → Go to (project name)**. This is your own script, so that is expected.
5. Copy the **Web app URL**. It starts with `https://script.google.com/macros/s/` and ends in `/exec`.

The tabs **Issues** and **Reviews** are created automatically when the first review arrives.

## 2. Connect the form to the sheet

1. Open **index.html** in a plain text editor (TextEdit in plain-text mode, VS Code, or Notepad).
2. Find this line near the bottom of the file:

   `const SCRIPT_URL = "PASTE_YOUR_WEB_APP_URL_HERE";`

3. Replace `PASTE_YOUR_WEB_APP_URL_HERE` with your Web app URL, keeping the quotes. Save the file.

## 3. Publish on GitHub Pages

1. Sign in to github.com and click **New repository**. Name it, for example, `translation-review`, set it to **Public**, and create it.
2. Click **Add file → Upload files**, drag in **index.html**, and click **Commit changes**.
3. Go to **Settings → Pages**. Under "Branch," choose **main** and **/(root)**, then click **Save**.
4. After a minute or two, the page shows your link, for example `https://yourname.github.io/translation-review/`. That's the link you send to reviewers.

## 4. Test it

Open the link, fill in a short review with one or two issues, and click **Submit review**. Then check the **Issues** and **Reviews** tabs in your sheet.

## Working with the results

- **Issues tab:** one row per suggested edit. Use the **Decision** dropdown (Accepted / Accepted with changes / Not accepted) and the **Note to translator** column. Sort or filter by Form, Page, Paragraph, or Severity.
- **Reviews tab:** one row per reviewer and form, with the 1–4 ratings, their average, and counts of critical, major, and minor issues.
- If a reviewer reopens a review and submits it again, their rows are replaced with the new version. Decisions you already entered are kept.
- To share results with the translator, share the sheet or use **File → Download → Microsoft Excel**.

## Good to know

- Reviewers don't need any account. Their drafts are saved in their own browser, so they should finish and resubmit on the same device.
- Anyone who has the link can submit, so send it only to your reviewers.
- **If you change Code.gs later:** choose **Deploy → Manage deployments → Edit (pencil) → Version: New version → Deploy**. This keeps the same URL.
- If submitting ever fails, reviewers can click **Download my review** and email you the CSV.

Elsa Pérez, PhD · CTIS
