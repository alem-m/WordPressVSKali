# Project 7 - WordPress Pen Testing

Time spent: 10+ hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pen Testing Report

### 1. Unauthenticated Stored Cross-Site Scripting (CVE-2015-3440)

- [x] Summary: An unathorized user/attacker can inject JavaScrip in WordPress comments, which will be triggered when the comment is viewed. If triggered by a logged-in administrator, under default settings the attacker can leverage the vulnerability to execute arbitrary code on the server via the plugin and theme editors.
  - Vulnerability types: XSS
  - Tested in version: 4.2
  - Fixed in version: 4.2.1
- [x] GIF Walkthrough: 
<img src='https://user-images.githubusercontent.com/91217813/198522301-196eeda8-ff20-4d27-ab4d-c92cc6a27bec.gif' width='850' />

- [x] Steps to recreate: 
    - Enter as a comment the following:
    ```
    <a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>
    ```
- [x] Affected source code:
  - Not Found
  
### 2. Authenticated Stored Cross-Site Scripting via Image Filename (CVE-2016-7168)

- [x] Summary: A persistent Cross-Site-Scripting vulnerability where an attacker can create a speciall crafted image file name, which when uploaded in WordPress, injects malicious JavaScript code into the application. This could lead to the theft of user session tokens or login credentials. Notice this involves social engineering.
  - Vulnerability types: XSS
  - Tested in version: 4.2
  - Fixed in version: 4.2.10
- [x] GIF Walkthrough: 
<img src='https://user-images.githubusercontent.com/91217813/198522301-196eeda8-ff20-4d27-ab4d-c92cc6a27bec.gif' width='850' />

- [x] Steps to recreate:
    - Add any new media file and change its name/title to `<img src=a onerror=alert(document.cookie)>.jpg`
    - Change the `Link to` option from the drop-down menu, and set it to `Attachment Page`
- [x] Affected source code:
  - [GitHub WordPress](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)

### 3. Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds (CVE-2017-6817)

- [x] Summary: Combined with the recent content injection vulnerability we found, it’s possible for a remote attacker to deface a random post on the site and store malicious Javascript code in it. This code would be executed when a visitors view the post and when anyone edits the post from the WordPress dashboard. As a result, an administrator tries to fix the defaced post, the would unknowingly trigger the malicious script, which could then be used to put a backdoor on the site and create new admin users.
  - Vulnerability types: XSS
  - Tested in version: 4.2
  - Fixed in version: 4.2.13
- [x] GIF Walkthrough: 
<img src='https://user-images.githubusercontent.com/91217813/198540301-67582958-73c7-4d05-805d-95c95f5c4021.gif' width='850'/>

- [x] Steps to recreate: 
    - Create a new post
    - Edit the post as Text, and embed the following:<br>
    ```[embed src='http://youtube.com/embed/12345\x3csvg onload=alert(1)\x3e'][/embed]```
    - View post
- [x] Affected source code:
  - [GitHub WordPress](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)

## Assets

Image for Report # 2 was downloaded from [mob.org](https://wallpaper.mob.org/)

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)
- [WordPress 4.2 core stored XSS](https://klikki.fi/wordpress-4-2-core-stored-xss/)
- [Packet Storm Security -- Persistent XSS](https://packetstormsecurity.com/files/131644/)
- [WordPress Unsafe Processing of File Names](https://sumofpwn.nl/advisory/2016/persistent_cross_site_scripting_vulnerability_in_wordpress_due_to_unsafe_processing_of_file_names.html)
- [Stored XSS in WordPressCore](https://blog.sucuri.net/2017/03/stored-xss-in-wordpress-core.html)

GIFs created with [ScreenToGif](https://www.screentogif.com/) for Windows



## License

    Copyright [2022] [alem-m]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
