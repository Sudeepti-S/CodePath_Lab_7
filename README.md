# Project 7 - WordPress Pentesting

Time spent: **10** hours spent in total

> Objective: Find, analyze, recreate, and document **Four vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required - Part of the Lab Challenge) Vulnerability One: Authenticated Stored Cross-Site Scripting via Image Filename
  - [ ] Summary: 
    - Vulnerability types: XSS Type: Reflected(Reflected XSS is when the script runs immediately in the victim's browser. The JavaScript being run would be included in the URL data or form data. It is called "reflected" because it bounces right back. In a well-designed attack, the user will not even notice that the script has run.)
    - Tested in version: 4.2
    - Fixed in version: 4.2.10
  - [ ] GIF Walkthrough:![alt text](https://github.com/Sudeepti-S/Week7CodePath/blob/master/XXS1.gif)
  - [ ] Steps to recreate: Go to the Media Library tab, upload a new image, change the title of the image to <script>alert('XSS!')</script>, scroll down and click on the “view attachment page” button
  
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
    (https://github.com/WordPress/WordPress/commit/c9e60dab176635d4bfaaf431c0ea891e4726d6e0)
1. (Required) Vulnerability Two: Authenticated Shortcode Tags Cross-Site Scripting (XSS) 
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.5
  - [ ] GIF Walkthrough: ![alt text](https://github.com/Sudeepti-S/Week7CodePath/blob/master/Vulnerability2.gif)
  - [ ] Steps to recreate: 
Go to the Pages tab,
Create a new page,
Under text mode,
Type in : Link[caption width="1" caption='<a href="' ">]</a><a href="http://onMouseOver='alert(1)'">HOVER HERE</a>>,
Go to the “Settings” tab ,
Then under “Permalinks” option, click on the “save changes” button,
Return to the Page and click on “View Page”  to see the alert

  - [ ] Affected source code: (https://wpvulndb.com/vulnerabilities/8768)
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
    - [Link 2](https://core.trac.wordpress.org/changeset/33359)
1. (Required) Vulnerability Three: Authenticated Shortcode Tags Cross-Site Scripting (XSS) via YouTube
  - [ ] Summary: 
    - Vulnerability types: XSS Type : XSS encoded scripts in URLs
    - Tested in version: 4.2
    - Fixed in version: 4.7.3
  - [ ] GIF Walkthrough: ![alt text](https://github.com/Sudeepti-S/Week7CodePath/blob/master/Vulnerability3.gif) 
  - [ ] Steps to recreate: 
Go to the Posts tab,
Go to youtube and search a video, 
copy the URL of that video under the visual setting, 
copy the link after discarding the text after “?v=“ in the URL,
Modify the link as such : <script>alert('XSS!')</script>,
Then copy the new link,
Go to the Insert/edit link option and copy that link into both the options(URL/Link text) 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
    1. (Required) Vulnerability Four: Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
  - [ ] Summary: 
    - Vulnerability types: XSS Type : XSS encoded scripts in URLs
    - Tested in version: 4.2
    - Fixed in version: 4.2.13, 4.7.3
  - [ ] GIF Walkthrough: ![alt text](https://github.com/Sudeepti-S/Week7CodePath/blob/master/Vulnerability4.gif) 
  - [ ] Steps to recreate: 
Go to the Pages tab 
Create a new page 
Under the text option, type  “<a href="[caption code=">]</a><a title=" onmouseover=alert('test') ">link</a>”
Update the page 
Then click, “View Page” 
  - [ ] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8)
    - [Link 2](https://wordpress.org/news/2017/03/wordpress-4-7-3-security-and-maintenance-release/)
    - [Link 3](https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8)
## Assets

All GIF's were created using Licecap. 

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)
- [References- Codepath] (https://guides.codepath.com/websecurity/Cross-Site-Scripting)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Initially, I expiereced a few challenges when setting up the lab environment. This was my first time using Vagrant and Licecap. However, that being said, after those learning curves, I was able to perform the attacks. I enjoyed learning more about XSS attacks through this lab. 

Cross-Site Scripting becomes possible when code puts user-supplied data in the response without sanitizing the data first. It gets its name because an attacker is able to run JavaScripts on someone else's site. Cross-Site Scripting is often abbreviated as "XSS".

It is ranked as #3 on Top 10 security threats by OWASP, and is the most common web application security flaw.

There are numerous ways that a hacker can provide JavaScript to a page. It depends on what incoming data is being output again without being properly sanitized. Once the hacker gets their JavaScript in the page response, the script will execute, usually for an unsuspecting user. The script can perform any number of actions, including stealing site cookies or session data. It succeeds because the browser believes that all JavaScript provided with the page is trustworthy.

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
