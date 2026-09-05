---
Content: DNS
Description: DNS (Domain Name System) translates human-readable domain names into IP addresses through a global, decentralized server network. Enables easy internet navigation by converting names like www.example.com to numeric addresses browsers can connect to.
Resources: 
- "[How DNS works: The animated video!](https://howdns.works/video/)"
- "[How DNS works (comic)](https://howdns.works/)"
---
#### DNS (Domain Name System) – Overview 
- **DNS** is basically the **phonebook of the internet**. It translates human-friendly domain names (like `google.com` or `cloudflare.com`) into machine-readable **IP addresses** (like `142.250.190.174`) so your browser can actually find and connect to websites.

- Without DNS → you'd have to remember and type IP addresses for every site.
---
#### How DNS Resolution Works – The Full Journey
- When you type a domain into your browser, a multi-step lookup happens (usually in milliseconds thanks to **caching**). 
- Here’s the classic uncached flow (worst-case / full resolution):
	1. **Browser / OS cache** → Checks if it already knows the IP (super fast, local). 
	2. **Stub resolver** (your device's tiny DNS client) → If not cached locally, asks the configured **recursive resolver** (usually your ISP’s or public like 8.8.8.8 / 1.1.1.1). 
	3. **Recursive resolver cache** → The resolver first checks *its own cache*. If hit → instant answer. 
	4. **Root name servers** (.) → If miss, asks one of the 13 root server clusters worldwide. → Root says: “I don’t know the IP, but here’s the address of the **TLD** server for .com / .org / etc.”
	5. **TLD name servers** (e.g. .com servers managed by Verisign) → Resolver asks the TLD. → TLD says: “I don’t have the IP, but here’s the **authoritative name server** for google.com.” 
	6. **Authoritative name servers** (set by the domain owner, e.g. Google’s own NS) → Final query. → They return the actual **IP address** (A record) or other records (CNAME, MX, etc.). 
	7. **Answer returned** → Resolver sends IP back to your device → browser connects → page loads.
- **Your shortcut reminder (perfect order!)**: **cache → os → resolver → root → TLD → Authoritative name servers → the answer (IP address)**
- Caching happens at **every step** — browser, OS, resolver, even sometimes upstream — so most real lookups are 1–2 steps max.

---
#### Quick Tips / Common Facts 
- Most people use **public resolvers** today: Cloudflare (1.1.1.1), Google (8.8.8.8), Quad9 (9.9.9.9) → faster + more private than ISP ones. 
- **TTL** (Time To Live) → Controls how long each cache layer keeps the record before asking again.
- Real lookups are usually **recursive** (resolver does all the work) vs **iterative** (client would have to ask each server — rare).