# Email Templates for Password Reset Functionality

This directory contains standardized email templates for password reset functionality to improve user experience and maintain consistent branding.

## Templates

### 1. password-reset-email.mjml

MJML template for initial password reset request emails.

**Format:** MJML (responsive email framework)

**Key Features:**
- Brand-customizable styling with variable placeholders
- Full dark mode support using CSS media queries
- Accessible, responsive design
- Security-focused messaging with clear warnings
- Comprehensive footer with privacy/support links
- Optional tracking pixel (commented out)
- Preheader text optimization for email clients
- Automatic dark/light mode rendering

### 2. temporary-password-email.html

HTML template for delivering temporary passwords to users.

**Format:** HTML with inline CSS

**Key Features:**
- Modern, clean design with brand customization
- Dark mode detection and automatic styling
- Bulletproof button compatibility across email clients
- Monospace password display for clarity
- Security and expiration notices
- Fallback plain-text links for accessibility
- VML button fallbacks for Outlook compatibility
- Fully responsive mobile design
- Security warning box with important guidelines

## Supported Variables

Both templates support the following variables that should be replaced before sending:

### Company & Branding
- `{{company_name}}` - Your company/product name
- `{{brand_primary}}` - Primary brand color (hex code, e.g., #007bff)
- `{{logo_url}}` - URL to your company logo
- `{{company_domain}}` - Your company domain (e.g., example.com)
- `{{company_address_line1}}` - First line of company address
- `{{company_address_line2}}` - Second line of company address

### User Information
- `{{user_first_name}}` - User's first name for personalization

### Functional URLs
- `{{reset_url}}` - Password reset/login URL
- `{{support_url}}` - Customer support center URL
- `{{security_tips_url}}` - Security guidelines page URL
- `{{privacy_url}}` - Privacy policy page URL
- `{{support_email}}` - Support email address

### Password Reset Specific
- `{{temporary_password}}` - The temporary password (for temporary-password-email.html only)
- `{{expires_in}}` - Expiration time (e.g., "24 hours", "1 hour")

### Optional
- `{{tracking_pixel_url}}` - Tracking pixel URL (currently commented out in both templates)

## Usage

### Using the MJML Template

The MJML template needs to be compiled to HTML before use:

```bash
# Install MJML CLI tool
npm install -g mjml

# Compile to HTML
mjml password-reset-email.mjml -o password-reset-email.html
```

### Variable Replacement

Replace all variables in the template with actual values before sending. Example in Java:

```java
String emailContent = readFileAsString("temporary-password-email.html");
emailContent = emailContent
    .replace("{{company_name}}", "PayBy")
    .replace("{{brand_primary}}", "#007bff")
    .replace("{{logo_url}}", "https://example.com/logo.png")
    .replace("{{user_first_name}}", user.getFirstName())
    .replace("{{reset_url}}", resetUrl)
    .replace("{{temporary_password}}", tempPassword)
    .replace("{{expires_in}}", "24 hours")
    .replace("{{support_url}}", "https://example.com/support")
    .replace("{{support_email}}", "support@example.com")
    .replace("{{company_domain}}", "example.com")
    .replace("{{security_tips_url}}", "https://example.com/security")
    .replace("{{privacy_url}}", "https://example.com/privacy")
    .replace("{{company_address_line1}}", "123 Business Street")
    .replace("{{company_address_line2}}", "City, State 12345");

// Send email
sendEmail(user.getEmail(), "Password Reset", emailContent);
```

## Implementation Notes

### Dark Mode Support

Both templates include automatic dark mode detection:
- Uses `@media (prefers-color-scheme: dark)` CSS media query
- Automatically adjusts colors for better readability in dark mode
- No additional configuration required

### Email Client Compatibility

The templates are tested and compatible with:
- Gmail (web, mobile)
- Outlook (web, desktop, mobile)
- Apple Mail
- Yahoo Mail
- Other major email clients

### Accessibility

Templates follow accessibility best practices:
- Semantic HTML structure
- Adequate color contrast ratios
- Alt text for images
- Keyboard-accessible links
- Screen reader friendly

### Security Best Practices

Both templates include:
- Clear security warnings
- Expiration notices
- Guidance on secure password practices
- Warning about not sharing credentials
- Links to security resources

### Responsive Design

Templates are fully responsive:
- Mobile-first approach
- Optimized for screens from 320px to 600px+
- Touch-friendly button sizes
- Readable font sizes on all devices

## Tracking Pixel (Optional)

Both templates include a commented-out tracking pixel section. To enable:

1. Uncomment the tracking pixel section at the bottom of the template
2. Replace `{{tracking_pixel_url}}` with your tracking service URL
3. Ensure privacy policy reflects email tracking

**Note:** Consider privacy regulations (GDPR, CCPA) before enabling tracking.

## Customization

### Colors

Adjust the primary brand color by changing the `{{brand_primary}}` variable. This affects:
- Buttons
- Links
- Accents

### Logo

Replace `{{logo_url}}` with your logo. Recommended specifications:
- Format: PNG with transparent background
- Dimensions: 300x100px (or similar aspect ratio)
- File size: < 100KB

### Content

You can customize the email copy by editing the template files directly, but maintain:
- Security warnings
- Clear call-to-action
- Contact information
- Legal footer

## Testing

Before deploying to production:

1. Test with actual variable values
2. Send test emails to multiple email clients
3. Check mobile rendering
4. Verify all links work correctly
5. Test dark mode appearance
6. Validate HTML (for temporary-password-email.html)
7. Compile and validate MJML (for password-reset-email.mjml)

## License

These templates are part of the PayBy-java SDK and follow the same license terms.

## Support

For questions or issues with these templates, please contact the development team or open an issue in the repository.
