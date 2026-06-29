# wp-security-checklist
A comprehensive WordPress security checklist organized by priority.

NOTE: Security is not a one-time task but an ongoing process. Test any changes on a staging site first, and always maintain current backups before making security modifications.

## 🔴 Critical Priority

### Core & Updates
- [ ] Keep WordPress core updated to latest version
- [ ] Enable automatic updates for minor releases
- [ ] Keep all themes updated (remove unused themes)
- [ ] Keep all plugins updated (remove unused plugins)
- [ ] Delete default "admin" username if it exists
- [ ] Remove unused user accounts

### Authentication
- [ ] Use strong passwords (12+ characters, mixed case, numbers, symbols)
- [ ] Enable Two-Factor Authentication (2FA) for all admin accounts
- [ ] Limit login attempts (install plugin like Limit Login Attempts Reloaded)
- [ ] Change default login URL from /wp-admin or /wp-login.php
- [ ] Set password strength requirements for all users

## 🟠 High Priority

### Hosting & Server
- [ ] Use a reputable WordPress-optimized hosting provider
- [ ] Enable SSL certificate (HTTPS everywhere)
- [ ] Keep PHP version updated (8.0+ recommended)
- [ ] Verify PHP memory limit is adequate (256M+)
- [ ] Configure proper file permissions:
    - Directories: 755
    - Files: 644
    - wp-config.php: 600

### File Protection
- [ ] Add security keys to wp-config.php (generate fresh salts)
- [ ] Change WordPress database table prefix from default "wp_"
- [ ] Disable file editing from dashboard:
  ```php
  define('DISALLOW_FILE_EDIT', true);
  ```
- [ ] Protect wp-config.php via .htaccess
- [ ] Block access to .htaccess file itself
- [ ] Disable directory browsing
- [ ] Hide WordPress version number

### Database Security
- [ ] Use strong database password
- [ ] Create database user with minimum required privileges
- [ ] Change database table prefix
- [ ] Regular database backups configured
- [ ] Secure phpMyAdmin access or remove if not needed

## 🟡 Medium Priority

### Security Plugins
- [ ] Install a WordPress security plugin (Wordfence, Sucuri, or iThemes Security)
- [ ] Configure firewall rules
- [ ] Enable malware scanning
- [ ] Set up security notifications/alerts
- [ ] Install spam protection (Akismet or similar)

### User Management
- [ ] Implement principle of least privilege for user roles
- [ ] Regularly audit user accounts
- [ ] Force strong passwords for all users
- [ ] Auto-logout idle users after set time period
- [ ] Monitor user activity logs

### Backup Strategy
- [ ] Implement automated daily backups
- [ ] Store backups off-site (cloud storage)
- [ ] Test backup restoration process monthly
- [ ] Backup both files and database
- [ ] Keep at least 30 days of backup history

## 🟢 Low Priority (But Important)

### Hardening wp-config.php
- [ ] Move wp-config.php one directory above root if possible
- [ ] Disable plugin/theme installation from dashboard:
  ```php
  define('DISALLOW_FILE_MODS', true);
  ```
- [ ] Set auto-save interval longer:
  ```php
  define('AUTOSAVE_INTERVAL', 300);
  ```
- [ ] Limit post revisions:
  ```php
  define('WP_POST_REVISIONS', 5);
  ```
- [ ] Force SSL for admin:
  ```php
  define('FORCE_SSL_ADMIN', true);
  ```

### .htaccess Security Rules
- [ ] Protect wp-includes directory
- [ ] Block access to xmlrpc.php if not needed
- [ ] Block author scans (prevent username enumeration)
- [ ] Restrict access by IP for admin area (if static IPs)
- [ ] Disable PHP execution in uploads directory

### Monitoring & Maintenance
- [ ] Set up uptime monitoring
- [ ] Enable error logging
- [ ] Regularly review security logs
- [ ] Schedule quarterly security audits
- [ ] Create incident response plan
- [ ] Remove inactive plugins/themes (not just deactivate)

### XML-RPC & REST API
- [ ] Disable XML-RPC if not using remote publishing
- [ ] Restrict REST API access for non-authenticated users
- [ ] Remove RSD (Really Simple Discovery) links
- [ ] Remove WLW Manifest links (Windows Live Writer)

## 📋 Regular Maintenance Schedule

### Weekly
- [ ] Review security plugin alerts
- [ ] Check for available updates
- [ ] Monitor user activity logs
- [ ] Scan for malware

### Monthly
- [ ] Change all passwords
- [ ] Review user accounts
- [ ] Test backup restoration
- [ ] Audit installed plugins/themes
- [ ] Check file integrity

### Quarterly
- [ ] Full security audit
- [ ] Review and update security policies
- [ ] Penetration testing (or vulnerability scan)
- [ ] Review hosting/server security
- [ ] Update incident response plan

## 🛡️ Emergency Response Checklist
If you suspect a hack:
- [ ] Take site offline immediately
- [ ] Change all passwords (hosting, FTP, database, WordPress)
- [ ] Scan for malware using security plugin
- [ ] Restore from clean backup
- [ ] Update everything (core, themes, plugins)
- [ ] Review access logs
- [ ] Notify users if data may have been compromised
- [ ] Consult security professional if needed

## Useful Code Snippets for wp-config.php

```php
// Disable file editing
define('DISALLOW_FILE_EDIT', true);

// Force SSL
define('FORCE_SSL_ADMIN', true);

// Disable plugin/theme installs
define('DISALLOW_FILE_MODS', true);

// Limit revisions
define('WP_POST_REVISIONS', 3);

// Auto-save interval
define('AUTOSAVE_INTERVAL', 300); // 5 minutes

// Empty trash
define('EMPTY_TRASH_DAYS', 7); // 7 days

// Disable debug mode in production
define('WP_DEBUG', false);
```



