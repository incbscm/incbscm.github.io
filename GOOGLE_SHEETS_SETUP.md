# Google Sheets Integration Setup Guide
## BSCM Contact Form

This guide will help you set up Google Sheets integration for the BSCM contact form, allowing all form submissions to be automatically saved to a Google Sheet.

## 📋 Prerequisites
- Google account
- Access to Google Sheets and Google Apps Script
- Basic understanding of copy/paste operations

## 🚀 Step-by-Step Setup

### Step 1: Create a Google Sheet
1. Go to [Google Sheets](https://sheets.google.com)
2. Create a new blank spreadsheet
3. Name it "BSCM Contact Form Submissions"
4. Copy the Sheet ID from the URL (the long string between `/d/` and `/edit`)
   - Example: `https://docs.google.com/spreadsheets/d/1ABC123DEF456GHI789JKL/edit`
   - Sheet ID: `1ABC123DEF456GHI789JKL`
   //11KRejFkX_uyMUCJ3vJlCKGFt5Py66vQkPPweHO0l1GQ/edit?gid=0#gid=0

### Step 2: Set Up Google Apps Script
1. Go to [Google Apps Script](https://script.google.com)
2. Click "New Project"
3. Delete the default `myFunction()` code
4. Copy and paste the entire contents of `google-apps-script.js` into the editor
5. Update the configuration:
   ```javascript
   const SHEET_ID = 'YOUR_SHEET_ID_HERE'; // Replace with your actual Sheet ID
   const SHEET_NAME = 'Contact Submissions'; // Keep this or change to preferred name
   ```
6. Save the project (Ctrl+S) and name it "BSCM Contact Form Handler"

### Step 3: Deploy the Web App
1. In Google Apps Script, click "Deploy" → "New deployment"
2. Click the gear icon ⚙️ next to "Type" and select "Web app"
3. Configure the deployment:
   - **Description**: "BSCM Contact Form Handler"
   - **Execute as**: "Me"
   - **Who has access**: "Anyone"
4. Click "Deploy"
5. **IMPORTANT**: Copy the Web App URL (it will look like: `https://script.google.com/macros/s/ABC123.../exec`)
6. Click "Done"
//https://script.google.com/macros/s/AKfycbwiNsfLGAPOc7TmKFyMkJof_RHP9YKJttshUTwMQQwDaTOe0nutEa2dBJEnF7-SOqtZ/exec

### Step 4: Update the Website
1. Open `contact-form.js` in your code editor
2. Find this line:
   ```javascript
   const GOOGLE_SCRIPT_URL = 'YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL_HERE';
   ```
3. Replace `YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL_HERE` with your actual Web App URL from Step 3

### Step 5: Test the Integration
1. Open your website's contact page
2. Fill out and submit the contact form
3. Check your Google Sheet - you should see a new row with the form data
4. Check your email (Tyler's email) for a notification

## 📊 Google Sheet Structure

The integration will automatically create these columns in your Google Sheet:
- **Timestamp**: When the form was submitted
- **Name**: Customer's name
- **Email**: Customer's email address
- **Phone**: Customer's phone number
- **Message**: Customer's message
- **IP Address**: Customer's IP (if available)
- **User Agent**: Customer's browser information

## 📧 Email Notifications

The system will automatically send email notifications to `Blackshear.Tyler@gmail.com` when forms are submitted. The email includes:
- All form data
- Submission timestamp
- IP address (if available)

## 🔧 Troubleshooting

### Common Issues:

**1. Form submissions not appearing in Google Sheet**
- Verify the Sheet ID is correct in `google-apps-script.js`
- Check that the Web App URL is correct in `contact-form.js`
- Ensure the Google Apps Script deployment has "Anyone" access

**2. "Google Apps Script URL not configured" error**
- Update the `GOOGLE_SCRIPT_URL` in `contact-form.js` with your actual Web App URL

**3. Permission errors**
- Make sure you're logged into the same Google account that created the script
- Re-deploy the Web App if needed

**4. Email notifications not working**
- Check the email address in `google-apps-script.js`
- Verify Gmail permissions in Google Apps Script

### Testing the Setup:
1. Run the `testSetup()` function in Google Apps Script to verify everything works
2. Check the execution log for any errors
3. Test the contact form on your website

## 🔒 Security Notes

- The Web App is set to "Anyone" access, but it only accepts POST requests with form data
- No sensitive information is exposed
- All data is stored securely in your Google Sheet
- Email notifications go only to the configured email address

## 📱 Features Included

✅ **Automatic Google Sheets logging**
✅ **Email notifications to Tyler**
✅ **Form validation and error handling**
✅ **Loading states and success/error messages**
✅ **Mobile-responsive design maintained**
✅ **Professional styling preserved**
✅ **Fallback email option if integration fails**

## 🆘 Support

If you encounter issues:
1. Check the Google Apps Script execution log for errors
2. Verify all URLs and IDs are correctly configured
3. Test with the `testSetup()` function in Google Apps Script
4. Ensure proper permissions are set for the Web App deployment

The contact form will maintain its professional appearance while seamlessly integrating with Google Sheets for efficient lead management.
