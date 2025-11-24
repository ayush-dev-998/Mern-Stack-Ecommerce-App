# Email Setup Instructions

To enable actual email sending, you need to:

1. Install nodemailer (already added to package.json):
   
   cd server
   npm install
   

2. Set up Gmail App Password:
   - Go to your Google Account settings
   - Enable 2-Step Verification
   - Generate an App Password for "Mail"
   - Copy the 16-character app password

3. Add environment variables to 'server/.env':
   
   EMAIL_USER=your_mail_id
   EMAIL_PASSWORD=your_16_character_app_password_here
   

4. The email service will automatically use these credentials to send emails from the mentioned mail id.

Note: If EMAIL_PASSWORD is not set, the service will still work but emails won't be sent (it will log to console instead).

