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
<img src='https://user-images.githubusercontent.com/91217813/198522301-196eeda8-ff20-4d27-ab4d-c92cc6a27bec.gif' width='850' height='500' />

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
<img src='https://user-images.githubusercontent.com/91217813/198522301-196eeda8-ff20-4d27-ab4d-c92cc6a27bec.gif' width='850' height='500' />

- [x] Steps to recreate:
    - Add any new media file and change its name/title to `<img src=a onerror=alert(document.cookie)>.jpg`
    - Change the `Link to` option from the drop-down menu, and set it to `Attachment Page`
- [x] Affected source code:
  - [GitHub WordPress](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)

### 3. (Required) Vulnerability Name or ID

- [ ] Summary: 
  - Vulnerability types:
  - Tested in version:
  - Fixed in version: 
- [ ] GIF Walkthrough: 
- [ ] Steps to recreate: 
- [ ] Affected source code:
  - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

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
