<h1>Email IMAP Backup Script</h1>

<p>
A Python-based IMAP email backup utility that downloads all mailbox folders
and stores emails locally in <strong>.mbox</strong> format.
Designed for scheduled backups and Synology NAS storage.
</p>

<hr/>

<h2>Features</h2>
<ul>
  <li>Connects securely to IMAP servers using SSL</li>
  <li>Automatically discovers all mail folders</li>
  <li>Backs up emails per folder into dated <code>.mbox</code> files</li>
  <li>Supports large mailboxes with progress logging</li>
  <li>Removes old backups automatically</li>
  <li>Detailed logging to file and console</li>
</ul>

<hr/>

<h2>Technology Stack</h2>
<ul>
  <li><strong>Language:</strong> Python 3</li>
  <li><strong>Protocols:</strong> IMAP over SSL</li>
  <li><strong>Storage:</strong> mbox format (standard mailbox archive)</li>
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

<h2>Folder Structure</h2>
<pre>
project/
│
├── backup_script.py
├── README.md
└── backups/
    ├── INBOX_20241218.mbox
    ├── Sent_20241218.mbox
    └── Archive_20241218.mbox
</pre>

<hr/>

<h2>Configuration</h2>

<p>
Edit the configuration section at the top of the script before running:
</p>

<pre>
IMAP_SERVER = "imap.host.com"
IMAP_PORT = 993
EMAIL_ADDRESS = "your_email@example.com"
EMAIL_PASSWORD = "your_password"
BACKUP_DIR = "/path/to/backup/directory"
LOG_FILE = "/path/to/log/file.log"
</pre>

<p>
<strong>Important:</strong> Use an app-specific password if your email provider supports it.
</p>

<hr/>

<h2>How It Works</h2>
<ol>
  <li>Connects to the IMAP server securely</li>
  <li>Retrieves all selectable mail folders</li>
  <li>Downloads every email in each folder</li>
  <li>Stores messages in a date-stamped <code>.mbox</code> file</li>
  <li>Logs progress and errors</li>
  <li>Deletes backups older than 30 days</li>
</ol>

<hr/>

<h2>Running the Script</h2>

<pre>
python backup_script.py
</pre>

<p>
The script will:
</p>
<ul>
  <li>Create backup folders if missing</li>
  <li>Generate daily backup files</li>
  <li>Output progress to console and log file</li>
</ul>

<hr/>

<h2>Backup Retention</h2>

<p>
Old backup files are automatically removed after <strong>30 days</strong>.
You can change this by editing:
</p>

<pre>
cleanup_old_backups(days_to_keep=30)
</pre>

<hr/>

<h2>Security Notes</h2>

<ul>
  <li>Credentials are stored in plain text — protect the script file</li>
  <li>No encryption is applied to backup files</li>
  <li>Use secure filesystem permissions</li>
  <li>Recommended to run on trusted servers only</li>
</ul>

<hr/>

<h2>Use Cases</h2>
<ul>
  <li>Personal email backups</li>
  <li>Small business mailbox archiving</li>
  <li>Synology NAS scheduled backups</li>
  <li>Disaster recovery preparation</li>
</ul>

<hr/>

<h2>License</h2>
<p>
This project is provided as-is for educational and personal use.
No warranty is provided.
</p>

