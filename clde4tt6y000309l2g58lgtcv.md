---
title: "df  -h  Reporting wrong volume usage?"
datePublished: Fri Jan 27 2023 06:17:32 GMT+0000 (Coordinated Universal Time)
cuid: clde4tt6y000309l2g58lgtcv
slug: df-h-reporting-wrong-volume-usage
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/GNyjCePVRs8/upload/d0c03c083f5e6a04db3f3b27e30fb2e2.jpeg
tags: ubuntu, linux, memory-management, df, disk-management

---

I was facing this issue this morning. My system was on for several weeks, and today it was showing disc full warnings. On brief analysis, I found that /var/log/ folder has grown massively. So cleaned up system logs, and ran [Bleachbit](https://www.bleachbit.org/download) as root user. Now in the Disk usage analyzer tool, it was showing my system is having enough disc space, and even the system was working as normal. But I was not able to download anything as I was still getting disk full notification. On googling I came to know that, even though I deleted but still those files may be open in some processes. To find it out , I ran `lsof -n | grep deleted` . In my case, Chrome was still referring to some of the deleted logs. A simple restart solved this issue.