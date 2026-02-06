# Mantis Lawn Services Website

A professional, modern website for your lawn care business with a contact form that saves submissions to Google Sheets.

## Files Included

- `index.html` - Home page
- `services.html` - Services page with details about lawn mowing, edging/trimming, and leaf removal
- `contact.html` - Contact form page
- `google-apps-script.js` - Backend script for handling form submissions

## Setup Instructions

### 1. Deploy the Website to GitHub Pages

1. Create a new repository on GitHub named `mantislawnkc.github.io` (or use your existing one)
2. Upload these three HTML files to the repository:
   - index.html
   - services.html
   - contact.html
3. The site will automatically be available at your custom domain once GitHub Pages verifies it

### 2. Set Up Google Apps Script (Contact Form Backend)

1. Go to https://script.google.com
2. Click "New Project"
3. Delete any existing code
4. Copy and paste the entire contents of `google-apps-script.js`
5. Click "Deploy" > "New deployment"
6. Click the gear icon ⚙️ next to "Select type" and choose "Web app"
7. Configure the deployment:
   - **Description**: "Mantis Lawn Contact Form"
   - **Execute as**: "Me"
   - **Who has access**: "Anyone"
8. Click "Deploy"
9. **IMPORTANT**: Copy the "Web app URL" that appears
10. Click "Done"

### 3. Connect the Form to Google Apps Script

1. Open `contact.html` in a text editor
2. Find this line (around line 241):
   ```javascript
   const SCRIPT_URL = 'YOUR_GOOGLE_SCRIPT_URL_HERE';
   ```
3. Replace `'YOUR_GOOGLE_SCRIPT_URL_HERE'` with your actual web app URL from step 2.9
4. Save the file
5. Upload the updated `contact.html` to your GitHub repository

### 4. (Optional) Enable Email Notifications

If you want to receive an email every time someone submits the contact form:

1. In your Google Apps Script, find this line (around line 105):
   ```javascript
   const YOUR_EMAIL = 'your-email@example.com';
   ```
2. Replace with your actual email address
3. Remove or comment out this line (around line 109):
   ```javascript
   return; // Remove this line to enable email notifications
   ```
4. Click "Deploy" > "Manage deployments"
5. Click the pencil icon ✏️ to edit
6. Change the version to "New version"
7. Click "Deploy"

### 5. Test the Contact Form

1. Go to your website: `www.mantislawnkc.com/contact.html`
2. Fill out the form and submit
3. Check your Google Drive - you should see a new spreadsheet called "Mantis Lawn - Contact Form Submissions"
4. The submission should appear in the spreadsheet
5. If you enabled email notifications, you should also receive an email

## Customization

### Change Colors

The website uses CSS variables for easy color customization. Edit the `:root` section at the top of each HTML file:

```css
:root {
    --primary: #2d5016;      /* Dark green */
    --primary-light: #4a7c2a; /* Medium green */
    --accent: #7cb342;        /* Bright green */
    --dark: #1a2f0d;         /* Very dark green */
    --light: #f4f7f0;        /* Light background */
    --text: #2c3e1f;         /* Text color */
    --text-light: #5a6b4d;   /* Light text */
}
```

### Add More Form Fields

To add fields to the contact form:

1. In `contact.html`, add the HTML for the new field in the form
2. In `google-apps-script.js`, update the `doPost` function to capture the new field
3. Update the spreadsheet headers in the `getOrCreateSheet` function

## Troubleshooting

**Form submissions not appearing in Google Sheets:**
- Make sure you copied the correct Web app URL
- Make sure you set "Who has access" to "Anyone" when deploying
- Check the Google Apps Script execution logs for errors

**GitHub Pages not working:**
- Verify DNS records are correct
- Make sure "Enforce HTTPS" is enabled in GitHub Pages settings
- Wait up to 24 hours for DNS propagation

**Website looks different than expected:**
- Clear your browser cache
- Make sure all files uploaded correctly to GitHub

## Support

If you need to make changes to the website or have questions, feel free to reach out!
