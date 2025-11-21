# Proxies

[**Direct link to heading**](./#how-proxies-works) **How Proxies works**

When sending a request to a website while on Burp/ZAP, you’re not connecting directly to the website’s server; you’re connecting to Burp/ZAP's proxy, which forwards your traffic. Every request you make passes through Burp/ZAP, allowing you to **intercept** and review it. When you modify a request, you’re effectively replacing the original with your edited version. Burp/ZAP then sends that modified request to the website, which has no visibility into the original request and only processes the version Burp/ZAP delivers.

[**Direct link to heading**](./#pre-configured-browser-in-burp-and-zap) **Pre-Configured Browser (In Burp & ZAP)**

In **Burp**'s Proxy → Intercept you can choose **Open Browser** to launch Burp’s built-in browser and automatically route its traffic through the proxy.

In **ZAP**, selecting the Firefox browser button opens a browser already configured to route traffic through ZAP.

#### [Direct link to heading](./#proxy-setup) Proxy Setup

For many tests you’ll want to use a real browser (Firefox is a common choice). It is easier to configure our browser's proxy with an [extension](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/) rather than the browser's own settings.

By configuring FoxyProxy to 127.0.0.1:8080, requests/responses will be intercepted by Burp/ZAP's default port (8080).

[**Direct link to heading**](./#installing-ca-certificate) **Installing CA Certificate**

Always install the web proxy's (Burp/ZAP) CA Certificates.

1. For Burp, we can do this by completing the steps above, navigating to http://burp, and downloading the CA Certificate. For ZAP go to Tools > Options > Network > Server Certificates.
2. Now install them within firefox, Certificates > Authorities > Check the CA trust boxes. Now all firefox traffic will route through the proxy (8080).

[PreviousFuzzing](../../../../../fuzzing.md) [NextBurp Suite](../../../../../burp-suite.md)

Last updated 7 days ago
