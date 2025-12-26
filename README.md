<h1>Email IMAP Backup & Restore Toolkit</h1>

<p>
A Python-based toolkit for <strong>backing up</strong>, <strong>searching</strong>, and <strong>restoring</strong>
emails from IMAP servers using standard <code>.mbox</code> archives.
Designed for reliability, manual recovery, and Synology NAS environments.
</p>

<hr/>

<h2>Overview</h2>

<p>
This project consists of <strong>two independent tools</strong>:
</p>

<ul>
  <li><strong>Email Backup Script</strong> – downloads and archives all IMAP folders</li>
  <li><strong>Email Restore Tool</strong> – searches backups and restores individual emails</li>
</ul>

<p>
Together, they provide a complete email disaster-recovery workflow.
</p>

<hr/>

<h2>Features</h2>

<ul>
  <li>Secure IMAP (SSL) connection</li>
  <li>Automatic discovery of all mailbox folders</li>
  <li>Per-folder <code>.mbox</code> backups with timestamps</li>
  <li>Search emails by subject, sender, body, or date</li>
  <li>Restore emails directly to IMAP server</li>
  <li>Export recovered emails as <code>.eml</code> files</li>
  <li>Automatic cleanup of old backups</li>
  <li>Detailed logging and progress reporting</li>
</ul>

<hr/>

<h2>Technology Stack</h2>

<ul>
  <li><strong>Language:</strong> Python 3</li>
  <li><strong>Protocol:</strong> IMAP over SSL</li>
  <li><strong>Archive Format:</strong> mbox</li>
  <li><strong>Libraries:</strong>
    <ul>
      <li><code>imaplib</code></li>
      <li><code>email</code></li>
      <li><code>mailbox</code></li>
      <li><code>logging</code></li>
    </ul>
  </li>
</ul>

<hr/>

<h2>Project Structure</h2>

<pre>
project/
│
├── backup_emails.py
├── restore_emails.py
├── README.md
└── backups/
    ├── INBOX_20241218.mbox
    ├── Sent_20241218.mbox
    └── Archive_20241218.mbox
</pre>

<hr/>

<h2>Email Backup Script</h2>

<h3>Purpose</h3>
<p>
Downloads all emails from every IMAP folder and stores them locally
as date-stamped <code>.mbox</code> files.
</p>

<h3>Configuration</h3>

<pre>
IMAP_SERVER = "imap.example.com"
IMAP_PORT = 993
EMAIL_ADDRESS = "user@example.com"
EMAIL_PASSWORD = "your_password"
BACKUP_DIR = "/path/to/backup"
LOG_FILE = "/path/to/log/file.log"
</pre>

<h3>Run Backup</h3>

<pre>
python backup_emails.py
</pre>

<h3>Retention Policy</h3>

<p>
Backups older than 30 days are automatically deleted.
</p>

<hr/>

<h2>Email Restore Tool</h2>

<h3>Purpose</h3>

<p>
Allows searching inside backup files and restoring individual emails.
Useful for recovering deleted or lost messages.
</p>

<h3>Capabilities</h3>

<ul>
  <li>Search by subject</li>
  <li>Search by sender</li>
  <li>Search email body content</li>
  <li>View full email source</li>
  <li>Restore to IMAP folder</li>
  <li>Save email as <code>.eml</code></li>
</ul>

<h3>Configuration</h3>

<pre>
BACKUP_DIR = "/volume1/mail-backup/mailboxes/example@domain.com"
IMAP_SERVER = "imap.example.com"
IMAP_PORT = 993
EMAIL_ADDRESS = "example@domain.com"
EMAIL_PASSWORD = "your_password"
</pre>

<h3>Run Restore Tool</h3>

<pre>
python restore_emails.py
</pre>

<h3>Restore Options</h3>

<ul>
  <li>Save recovered email as <code>.eml</code></li>
  <li>Restore directly to IMAP (e.g. INBOX)</li>
  <li>View raw email content</li>
</ul>

<hr/>

<h2>Security Notes</h2>

<ul>
  <li>Credentials are stored in plain text</li>
  <li>No encryption at rest for backups</li>
  <li>Protect filesystem permissions</li>
  <li>Recommended for trusted environments only</li>
</ul>

<hr/>

<h2>Use Cases</h2>

<ul>
  <li>Email disaster recovery</li>
  <li>Synology NAS scheduled backups</li>
  <li>Mailbox auditing and forensics</li>
  <li>Manual recovery of deleted emails</li>
</ul>

<hr/>

<h2>License</h2>

<p>
Provided as-is for personal and administrative use.
No warranty is provided.
</p>
