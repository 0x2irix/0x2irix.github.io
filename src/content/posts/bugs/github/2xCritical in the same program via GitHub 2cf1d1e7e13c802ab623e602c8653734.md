---
title: 2xCritical in the same program via GitHub
published: 2025-12-20
description: ""
image: "kurama.jpg"
tags: ["bugs", "Web", "recon", "db", "information disclosure"]
category: Bugs
draft: false
---

## **Leaked DB credentials via Github**

During the reconnaissance phase, I was hunting on GitHub using targeted keywords in an attempt to identify sensitive information. During this process, I discovered a useful website that generates GitHub dorks based on the target organization’s name. By simply entering the organization name, the tool provides pre-built dorks and redirects the user directly to GitHub search results. This allowed me to review repositories that potentially contained sensitive data. While analyzing the results, I identified exposed credentials, which included valid **MongoDB credentials.**

![Screenshot 2025-12-20 190135.png](Screenshot_2025-12-20_190135.png)

**GitHub Dork Helper:** https://vsec7.github.io/

---

## **Information Disclosure lead to Unauthorized Access via GitHub**

While going through Github search I discovered a public repository which contains Secret API Key of XXXXdeveloper.

![Screenshot_2024-11-20_210113.png](Screenshot_2024-11-20_210113.png)

take user_id and api_secret and separate it by this mark `:` then encode him to base64 

```bash
curl -X POST https://XXXXXXXXXXXXXX/collection/token/ \
-H "Authorization: Basic XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX" \
-H "Ocp-Apim-Subscription-Key: XXXXXXXXXXXXXXXXXXdfb" \
-d "grant_type=client_credentials"
```

the output is json and after decrypt this output i found this is refer to sessionId, expires, client id that's meaning this key is valid and i can login into this account

![Screenshot_2024-11-20_211350.png](Screenshot_2024-11-20_211350.png)

## HackerOne proof:

![image.png](image.png)