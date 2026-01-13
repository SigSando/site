---
layout: post
title: "RSS reader basics"
categories: Security
parent: Security 101
nav_order: 2
nav_exclude: false
---

{: .text-center }
# RSS readers

![rssin](/site/assets/rssin.png){: width="auto" height="auto" }

###### Posted ***June 22, 2024***

{: .warning }
RSS readers (Really Simple Syndication)

RSS readers are a good way to watch streams of information especially cyber news. I use YARR (its on github) and below is a basic .opml file you can import to see my config. 

Pretty useful if you ask me.

----

{: .text-center }
## <span style="color: royalblue; font-weight: bolder;">Basic OPML config</span>

```yaml
<?xml version="1.0" encoding="UTF-8"?>
<opml version="1.1">
<head><title>subscriptions</title></head>
<body>
  <outline text="Bulletins/Recent Events">
    <outline type="rss" text="bellingcat" xmlUrl="https://www.bellingcat.com/feed/" htmlUrl="https://www.bellingcat.com/"/>
    <outline type="rss" text="Biz &amp; IT - Ars Technica" xmlUrl="https://feeds.arstechnica.com/arstechnica/technology-lab" htmlUrl="https://arstechnica.com"/>
    <outline type="rss" text="BleepingComputer" xmlUrl="https://www.bleepingcomputer.com/feed/" htmlUrl="https://www.bleepingcomputer.com/feed/"/>
    <outline type="rss" text="CrowdStrike Holdings, Inc. Events" xmlUrl="https://ir.crowdstrike.com/rss/events.xml" htmlUrl="https://ir.crowdstrike.com/"/>
    <outline type="rss" text="darkreading" xmlUrl="https://www.darkreading.com/rss.xml" htmlUrl="https://www.darkreading.com/rss.xml"/>
    <outline type="rss" text="security - Ars Technica" xmlUrl="https://arstechnica.com/tag/security/feed/" htmlUrl="https://arstechnica.com"/>
    <outline type="rss" text="Security Latest" xmlUrl="https://www.wired.com/feed/category/security/latest/rss" htmlUrl="https://www.wired.com/feed/category/security/latest/rss"/>
    <outline type="rss" text="The criticality of introducing AI into mission-critical systems | CIO" xmlUrl="https://www.cio.com/feed/" htmlUrl="https://www.cio.com"/>
    <outline type="rss" text="The Hacker News" xmlUrl="https://feeds.feedburner.com/TheHackersNews" htmlUrl="https://feeds.feedburner.com/TheHackersNews"/>
  </outline>
  <outline text="CVE Feeds">
    <outline type="rss" text="Latest Newsroom" xmlUrl="https://cvefeed.io/rssfeed/newsroom.xml" htmlUrl="https://cvefeed.io/rssfeed/newsroom.xml"/>
    <outline type="rss" text="Latest Vulnerabilities" xmlUrl="https://cvefeed.io/rssfeed/latest.xml" htmlUrl="https://cvefeed.io/rssfeed/latest.xml"/>
  </outline>
  <outline text="Gov">
    <outline type="rss" text="Alerts" xmlUrl="https://us-cert.cisa.gov/ncas/current-activity.xml" htmlUrl="https://www.cisa.gov/"/>
    <outline type="rss" text="Cyber Security Advisories - MS-ISAC" xmlUrl="https://www.cisecurity.org/feed/advisories" htmlUrl="https://www.cisecurity.org/feed/advisories"/>
    <outline type="rss" text="Cybersecurity Insights" xmlUrl="https://www.nist.gov/blogs/cybersecurity-insights/rss.xml" htmlUrl="https://www.nist.gov/blogs/cybersecurity-insights/rss.xml"/>
    <outline type="rss" text="ICS Advisories" xmlUrl="https://us-cert.cisa.gov/ics/advisories/advisories.xml" htmlUrl="https://www.cisa.gov/"/>
    <outline type="rss" text="SANS Internet Storm Center, InfoCON: green" xmlUrl="https://isc.sans.edu/rssfeed_full.xml" htmlUrl="https://isc.sans.edu"/>
  </outline>
  <outline text="legal">
    <outline type="rss" text="Policy - Ars Technica" xmlUrl="https://feeds.arstechnica.com/arstechnica/tech-policy" htmlUrl="https://arstechnica.com"/>
  </outline>
  <outline text="Ransomware Leak Sites">
    <outline type="rss" text="Ransomware.live RSS Feed" xmlUrl="https://ransomware.live/rss" htmlUrl="https://ransomware.live/rss"/>
  </outline>
</body>
</opml>
```

