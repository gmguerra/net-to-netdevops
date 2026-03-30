# Azure Web Application Firewall

Resource that provides centralized protection of the web applications from common exploits and vulnerabilities. Protects applications from attacks such as SQL injection adn cross-site scripting. 

Web Apps shows to the users only what is programmed to show, but there are exploits and malicious actors that make this task difficult to protect the apps from the code. For this reason, WAF is created, as an easier, faster and more efficient way to protect the web applications. 

Azure WAF sits between the internet and the Web App, preventing malicious actors to use common exploits. Microsoft updates WAF to make it capable of defending against new threats. Also, WAF provides better assurance of protection against threats and intrusions. WAF solution can react to security threat faster by centrally patching a known vulnerability, instead of securing each individual web application. 

### WAF Policy Modes

There are two: 
- Detection: this is the default mode, when WAF doesn't block any requests but logs them.
- Prevention: Requests that match a security rule are both logged and blocked. 

The WAF works with App gateway, Azure Front Door service, and the Azure CDN service. 

### Microsoft managed rule sets, rule groups and rules

Microsoft includes in WAF the threat intelligence based rule groups, CVE rule groups and core rule groups (CRS) so WAF stays up to date to latest threats. Security rule groups is a collection of rules, and a managed rule set is a collection of rule groups, which is the case of Microsoft managed ones.  Rules are designed to recognize and prevent a particular threat. 

Common threats the WAF checks are:
- Cross-site scripting: when malicious code is sent to another user's web browser by the web app.
- Local file inclusion: exploits of vulnerabilities in a server's handling of include statements, often in PHP.
- PHP injection attacks: text specially configured to trick the server into running PHP commands.
- Remote command execution: malicious actor tricks the server into running OS commands.
- Session fixation: Web app vulnerability that allows the attacker to obtain a valid session ID. 
- SQL injection: when text specially configured is inserted in web forms to trick the server into running SQL commands. 
- Protocol attackers: when specially configured text is inserted into an HTTP/HTTPS request header. 