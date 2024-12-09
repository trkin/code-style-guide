---
title: "VS code tips"
weight: 1
description: >-
     Tips for Visual studio
---

# Enable html formating

## To make the code indent and formatted correctly, install an ERB Formatter/Beautify extension in VS Code.

After that, add the following to your **settings.json**:

"[erb]": {
  "editor.defaultFormatter": "aliariff.vscode-erb-beautify",
    "editor.formatOnSave": true
  },
  "editor.formatOnSave": true
}

# For optimal rendering of email templates, it is recommended to follow these steps:

# 1. Stick to Table-Based Layouts
Use Tables: Most email clients, including Outlook, handle table-based layouts more consistently. Use nested tables for complex layouts instead of relying on CSS positioning.
Avoid Divs and Floats: While convenient for web design, divs and floats can lead to inconsistent rendering across clients.

# 2. Inline CSS for Styling
Inline Your Styles: Many email clients strip out external and embedded styles, so inline your CSS. Tools like Premailer or Juice can help automate this.
Limit CSS: Stick to simple styling, like background colors, font styles, padding, and margins. Avoid CSS3 properties, like animations and transitions, which are unsupported in many clients.

# 3. Responsive Design with Media Queries
Mobile-First Design: Design for mobile first, then adapt for desktop. About 50% of emails are opened on mobile devices, so starting with mobile ensures a good experience for most users.
Use Media Queries: Media queries work well in most modern mobile clients, enabling you to adjust font sizes, hide or show elements, and stack columns. Be aware that some email clients like Gmail’s mobile app have limited media query support.

# 4. Keep Email Width Around 500/600px
Standard Width: A 600px width is widely accepted for emails and ensures good readability on both desktop and mobile.
Flexible Layouts for Mobile: Use percentage-based widths for images and tables where possible to maintain responsiveness.

# 5. Use System Fonts for Consistency
Web-Safe Fonts: Stick to common fonts like Arial, Verdana, and Times New Roman. Custom fonts often aren't supported and can default to unreadable styles.
Fallback Fonts: If you use custom fonts, specify a fallback font to ensure readability if the custom font isn’t displayed.

# 6. Optimize Images and Use Alt Text
Compressed Images: Compress images to reduce file size, optimizing load time for users and reducing the likelihood of images being blocked.
Alt Text: Include alt text for all images to convey key messages when images are blocked by default.

# 7. Minimize Interactive Elements and JavaScript
Limit Interactive Features: Many email clients don’t support JavaScript or CSS3. Avoid JavaScript and advanced CSS features like hover effects or animations.
Buttons Instead of Links: Use buttons with inline CSS for CTAs instead of plain text links to make them more visible and engaging.

# 8. Include a Plain Text Version
Multi-Part Email: Send both HTML and plain-text versions. This improves deliverability and ensures compatibility with all email clients.
Simple Text Layout: Keep the plain text version readable with line breaks, headers, and links to replicate the HTML email content where possible.

# 9. Test Across Clients and Devices
Cross-Client Testing: Use tools like Litmus, Email on Acid, or manual testing with actual email accounts to see how the email renders across different clients.
Mobile and Dark Mode Testing: Check how your email appears on mobile devices and in dark mode, as many email clients and devices offer dark mode themes.
  
# 10. Windows 10
When it comes to Windows 10, instead of the background image, it is better to use vectors (this is the only way for the image to be displayed).
