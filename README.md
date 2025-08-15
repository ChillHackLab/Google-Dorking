# Google Dorks Collection for Security Research

## Overview
This repository contains a curated collection of Google Dorks (advanced search queries) designed for security researchers, penetration testers, and bug bounty hunters. These dorks help identify exposed sensitive information, vulnerable servers, configuration files, database dumps, and more on the internet. The dorks are compiled from various sources, including bug bounty wordlists, SQL injection lists, and general Google dorking guides.

**Important Disclaimer:** These tools are for educational and ethical purposes only. Use them responsibly and only on systems you have permission to test. Unauthorized access or exploitation is illegal and unethical. Always comply with laws and obtain explicit consent before performing any scans or tests.

## Categories
The dorks are categorized for ease of use. Each category includes examples from the provided documents.

### 1. Exposed Configuration Files (e.g., Configs with Credentials or API Keys)
These target files like .env, config.php, or INI files that may contain secrets.
- `intitle:"index of" ("config.php" OR "wp-config.php" OR "database-config.php" OR "settings.conf" OR "appsettings.json") AND ("database" OR "credentials") -intitle:"documentation" -filetype:pdf`
- `ext:env | ext:yaml | ext:json "DB_PASSWORD"`
- `filetype:ini intext:env.ini`
- `ext:ini Version=4.0.0.4 password`
- `intitle:"index of" config.yml`
- `filetype:env "DB_PASSWORD"`
- `filetype:conf intext:"password"`
- `inurl:/wp-content/plugins/revslider/`
- `filetype:inc intext:mysql_connect password -please -could -port`
- `inurl:/admin/config.php`
- `intitle:"Error using Hypernews" "Server Software"`
- `intitle:"eXist Database Administration" -demo`
- `intitle:"EZPartner" -netpond`
- `intitle:"inc. vpn 3000 concentrator"`

### 2. Open Directories and Backup Files (e.g., Public Folders with Sensitive Content)
These reveal indexed directories with backups or passwords.
- `intitle:"index of" "parent directory" site:yourcompany.com`
- `intitle:"index of" ("passwords.txt" OR "leaked-passwords.csv" OR "passwords.bak" OR "keyfile") -git -github -gitlab -bitbucket`
- `parent directory /appz/ -xxx -html -htm -php -shtml -opendivx -md5 -md5sums`
- `site:s3.amazonaws.com intitle:"index of" ("bucket" OR "files" OR "public" OR "documents" OR "images")`
- `intitle:"Index of" -inurl:(jsp|pl|php|html|aspx|htm|cf|shtml) -inurl:(listen77|mp3raid|mp3toss|mp3drug|index_of|wallywashis)`
- `intitle:"index of" password.txt`
- `intitle:"index of" error.log`
- `intitle:index of .git`
- `intitle:"index of" inurl:ftp`
- `intitle:"index of" /admin`
- `intitle:"index of" wp-admin`
- `intitle:"Index of /" password.txt`
- `"index of" inurl:wp-content/`
- `intitle:"index of" "Index of /" password.txt`
- `allinurl:".r{}_vti_cnf/"`
- `intitle:"index of" inurl:backup`

### 3. Database Dumps and Logs (e.g., SQL Backups or Error Logs with Data)
These locate database exports or logs with sensitive data.
- `filetype:sql "dump" OR "backup"`
- `ext:mdb inurl:_.mdb inurl:fpdb shop.mdb`
- `ext:log "Software: Microsoft Internet Information Services _._"`
- `filetype:txt intext:"password"`
- `filetype:sql "# dumping data for table"`
- `filetype:sql "# dumping data for table “”` PASSWORD` varchar ”`
- `filetype:sql intext:wp_users PHPMyAdmin`
- `filetype:sql "# for write privileges execute"`
- `filetype:sql "PASSWORD()"`
- `filetype:sql "insert into" (pass|passwd|password)`
- `filetype:sql password`
- `filetype:log inurl:”access.log”`
- `filetype:sql inurl:wp-content/backup-*`
- `intext:”phpMyAdmin MySQL-Dump” filetype:sql`
- `inurl:admin filetype:log`
- `inurl:log -intext:log ext:log inurl:wp-`

### 4. Login Pages and Admin Panels (e.g., Entry Points for Brute-Force Attacks)
These find unprotected login forms.
- `inurl:"/login.php" OR inurl:"/admin.php" OR inurl:"/signin.php" OR inurl:"/user/login" intitle:"login" OR intitle:"admin" OR intitle:"portal" OR intext:"username" AND intext:"password"`
- `inurl:admin intitle:"login" site:yourcompany.com`
- `inurl:login OR inurl:admin OR inurl:signin`
- `inurl:admin login`
- `inurl:/index.php/admin`
- `inurl:"/user/login" "Powered by Drupal"`
- `intitle:"login" "admin"`
- `inurl:admin login`
- `intitle:"phpMyAdmin" "Welcome to phpMyAdmin ***"`
- `inurl:"dbadmin"`
- `inurl:/phpmyadmin/index.php`
- `intext:”Welcome to phpMyAdmin”`
- `intitle:”Login — WordPress”`
- `inurl:/phpPgAdmin/index.php`
- `intext:”phpPgAdmin — Login”`
- `intitle:"Employee Intranet Login"`
- `intitle:"ePowerSwitch Login"`
- `intitle:"Cisco CallManager User Options Log On" "Please enter your User ID and Password in the spaces provided below and click the Log On button to co`
- `intitle:"ColdFusion Administrator Login"`

### 5. Leaked Credentials and Sensitive Documents (e.g., Docs with Passwords)
These search for credentials in files or pastes.
- `site:pastebin.com intext:"email" AND intext:"password" OR intext:"credentials" OR intext:"login" OR intext:"user:pass"`
- `ext:(doc | pdf | xls | txt | ps | rtf | odt | sxw | psw | ppt | pps | xml) (intext:confidential salary | intext:"budget approved") inurl:confidential`
- `filetype:pdf "strictly confidential" site:yourcompany.com`
- `filetype:pdf "Confidential"`
- `site:drive.google.com confidential`
- `filetype:txt @gmail.com OR @yahoo.com OR @hotmail.com OR @aol.com`
- `filetype:txt "login" site:yourcompany.com`
- `ext:pwd inurl:(service | authors | administrators | users) "# -FrontPage-"`
- `allintitle: restricted filetype:doc site:gov`
- `intitle:"curriculum vitae" filetype:doc`
- `filetype:txt "password"`

### 6. Vulnerable Servers and Applications (e.g., Misconfigured Servers)
These identify servers with known vulnerabilities.
- `intitle:"Welcome to Windows 2000 Internet Services"`
- `inurl:index.php?id=`
- `inurl:/index.php?option=com_joomla`
- `intitle:"Apache Tomcat" intext:"If you're seeing this, you've successfully installed Tomcat"`
- `intext:"Warning: mysql_connect()" intext:"on line" filetype:php`
- `intext:”Error Message” intext:”MySQL server” intext:”on * using password:”`
- `inurl:phpinfo.php`
- `inurl:"/cgi-bin/" intext:"default password"`
- `intitle:"Apache2 Ubuntu Default Page: It works"`
- `intitle:"mongodb status" intext:"topologyVersion"`
- `intitle:"Kibana" intext:"Welcome to Elastic"`
- `intitle:"Dashboard [Jenkins]"`
- `intitle:"GitLab"`
- `intitle:"Error Occurred While Processing Request" +WHERE (SELECT|INSERT) filetype:cfm`
- `intitle:"Error Occurred" "The error occurred in" filetype:cfm`
- `intitle:"Execution of this script not permitted"`
- `intitle:"Default PLESK Page"`
- `intitle:"Dell Remote Access Controller"`

## Usage
1. **Copy a dork** and paste it into Google Search.
2. **Refine searches**: Replace placeholders like `site:yourcompany.com` with your target domain.
3. **Tools**: Use tools like GHunt or dork-cli for automation, but ensure ethical use.
4. **Best Practices**: Limit results with `-site:example.com` to exclude irrelevant sites.

## Contribution
Feel free to submit pull requests with new dorks or improvements.

## License
This collection is provided under the MIT License.

---

# Google Dorks 安全研究搜尋集合（繁體中文）

## 概述
此儲存庫包含一系列精心整理的 Google Dorks（進階搜尋查詢），專為安全研究人員、滲透測試人員和漏洞賞金獵人設計。這些 dorks 有助於識別網際網路上暴露的敏感資訊、易受攻擊的伺服器、設定檔、資料庫轉儲等。這些 dorks 彙編自各種來源，包括漏洞賞金字詞清單、SQL 注入清單和一般 Google dorking 指南。

**重要免責聲明：** 這些工具僅用於教育和道德目的。請負責任地使用，並僅在您有權測試的系統上使用。未經授權的存取或利用是非法的且不道德的。請始終遵守法律，並在執行任何掃描或測試前取得明確同意。

## 分類
dorks 已分類以便使用。每個分類包含提供的文件中的範例。

### 1. 暴露的設定檔（例如，包含憑證或 API 金鑰的設定檔）
這些針對像 .env、config.php 或 INI 檔，可能包含機密資訊。
- `intitle:"index of" ("config.php" OR "wp-config.php" OR "database-config.php" OR "settings.conf" OR "appsettings.json") AND ("database" OR "credentials") -intitle:"documentation" -filetype:pdf`
- `ext:env | ext:yaml | ext:json "DB_PASSWORD"`
- `filetype:ini intext:env.ini`
- `ext:ini Version=4.0.0.4 password`
- `intitle:"index of" config.yml`
- `filetype:env "DB_PASSWORD"`
- `filetype:conf intext:"password"`
- `inurl:/wp-content/plugins/revslider/`
- `filetype:inc intext:mysql_connect password -please -could -port`
- `inurl:/admin/config.php`
- `intitle:"Error using Hypernews" "Server Software"`
- `intitle:"eXist Database Administration" -demo`
- `intitle:"EZPartner" -netpond`
- `intitle:"inc. vpn 3000 concentrator"`

### 2. 開放目錄和備份檔（例如，包含敏感內容的公開資料夾）
這些揭示索引目錄，包含備份或密碼。
- `intitle:"index of" "parent directory" site:yourcompany.com`
- `intitle:"index of" ("passwords.txt" OR "leaked-passwords.csv" OR "passwords.bak" OR "keyfile") -git -github -gitlab -bitbucket`
- `parent directory /appz/ -xxx -html -htm -php -shtml -opendivx -md5 -md5sums`
- `site:s3.amazonaws.com intitle:"index of" ("bucket" OR "files" OR "public" OR "documents" OR "images")`
- `intitle:"Index of" -inurl:(jsp|pl|php|html|aspx|htm|cf|shtml) -inurl:(listen77|mp3raid|mp3toss|mp3drug|index_of|wallywashis)`
- `intitle:"index of" password.txt`
- `intitle:"index of" error.log`
- `intitle:index of .git`
- `intitle:"index of" inurl:ftp`
- `intitle:"index of" /admin`
- `intitle:"index of" wp-admin`
- `intitle:"Index of /" password.txt`
- `"index of" inurl:wp-content/`
- `intitle:"index of" "Index of /" password.txt`
- `allinurl:".r{}_vti_cnf/"`
- `intitle:"index of" inurl:backup`

### 3. 資料庫轉儲和日誌（例如，SQL 備份或包含資料的錯誤日誌）
這些定位資料庫匯出或包含敏感資料的日誌。
- `filetype:sql "dump" OR "backup"`
- `ext:mdb inurl:_.mdb inurl:fpdb shop.mdb`
- `ext:log "Software: Microsoft Internet Information Services _._"`
- `filetype:txt intext:"password"`
- `filetype:sql "# dumping data for table"`
- `filetype:sql "# dumping data for table “”` PASSWORD` varchar ”`
- `filetype:sql intext:wp_users PHPMyAdmin`
- `filetype:sql "# for write privileges execute"`
- `filetype:sql "PASSWORD()"`
- `filetype:sql "insert into" (pass|passwd|password)`
- `filetype:sql password`
- `filetype:log inurl:”access.log”`
- `filetype:sql inurl:wp-content/backup-*`
- `intext:”phpMyAdmin MySQL-Dump” filetype:sql`
- `inurl:admin filetype:log`
- `inurl:log -intext:log ext:log inurl:wp-`

### 4. 登入頁面和管理面板（例如，用於暴力攻擊的入口點）
這些找到未受保護的登入表單。
- `inurl:"/login.php" OR inurl:"/admin.php" OR inurl:"/signin.php" OR inurl:"/user/login" intitle:"login" OR intitle:"admin" OR intitle:"portal" OR intext:"username" AND intext:"password"`
- `inurl:admin intitle:"login" site:yourcompany.com`
- `inurl:login OR inurl:admin OR inurl:signin`
- `inurl:admin login`
- `inurl:/index.php/admin`
- `inurl:"/user/login" "Powered by Drupal"`
- `intitle:"login" "admin"`
- `inurl:admin login`
- `intitle:"phpMyAdmin" "Welcome to phpMyAdmin ***"`
- `inurl:"dbadmin"`
- `inurl:/phpmyadmin/index.php`
- `intext:”Welcome to phpMyAdmin”`
- `intitle:”Login — WordPress”`
- `inurl:/phpPgAdmin/index.php`
- `intext:”phpPgAdmin — Login”`
- `intitle:"Employee Intranet Login"`
- `intitle:"ePowerSwitch Login"`
- `intitle:"Cisco CallManager User Options Log On" "Please enter your User ID and Password in the spaces provided below and click the Log On button to co`
- `intitle:"ColdFusion Administrator Login"`

### 5. 洩露憑證和敏感文件（例如，包含密碼的文件）
這些搜尋檔案或貼文中的憑證。
- `site:pastebin.com intext:"email" AND intext:"password" OR intext:"credentials" OR intext:"login" OR intext:"user:pass"`
- `ext:(doc | pdf | xls | txt | ps | rtf | odt | sxw | psw | ppt | pps | xml) (intext:confidential salary | intext:"budget approved") inurl:confidential`
- `filetype:pdf "strictly confidential" site:yourcompany.com`
- `filetype:pdf "Confidential"`
- `site:drive.google.com confidential`
- `filetype:txt @gmail.com OR @yahoo.com OR @hotmail.com OR @aol.com`
- `filetype:txt "login" site:yourcompany.com`
- `ext:pwd inurl:(service | authors | administrators | users) "# -FrontPage-"`
- `allintitle: restricted filetype:doc site:gov`
- `intitle:"curriculum vitae" filetype:doc`
- `filetype:txt "password"`

### 6. 易受攻擊的伺服器和應用程式（例如，設定錯誤的伺服器）
這些識別具有已知漏洞的伺服器。
- `intitle:"Welcome to Windows 2000 Internet Services"`
- `inurl:index.php?id=`
- `inurl:/index.php?option=com_joomla`
- `intitle:"Apache Tomcat" intext:"If you're seeing this, you've successfully installed Tomcat"`
- `intext:"Warning: mysql_connect()" intext:"on line" filetype:php`
- `intext:”Error Message” intext:”MySQL server” intext:”on * using password:”`
- `inurl:phpinfo.php`
- `inurl:"/cgi-bin/" intext:"default password"`
- `intitle:"Apache2 Ubuntu Default Page: It works"`
- `intitle:"mongodb status" intext:"topologyVersion"`
- `intitle:"Kibana" intext:"Welcome to Elastic"`
- `intitle:"Dashboard [Jenkins]"`
- `intitle:"GitLab"`
- `intitle:"Error Occurred While Processing Request" +WHERE (SELECT|INSERT) filetype:cfm`
- `intitle:"Error Occurred" "The error occurred in" filetype:cfm`
- `intitle:"Execution of this script not permitted"`
- `intitle:"Default PLESK Page"`
- `intitle:"Dell Remote Access Controller"`

## 使用方法
1. **複製 dork** 並貼到 Google 搜尋中。
2. **精煉搜尋**：將像 `site:yourcompany.com` 的佔位符替換為您的目標網域。
3. **工具**：使用像 GHunt 或 dork-cli 的工具進行自動化，但確保道德使用。
4. **最佳實務**：使用 `-site:example.com` 限制結果以排除無關網站。

## 貢獻
歡迎提交拉取請求以新增 dorks 或改進。

## 授權
此集合以 MIT 授權提供。
