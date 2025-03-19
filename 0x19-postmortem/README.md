# **Postmortem: Web Server Outage**

## **Issue Summary**
- **Duration:** March 10, 2025, 02:30 AM - March 10, 2025, 05:45 AM (UTC)
- **Impact:** Website and API services were completely unavailable. Approximately 85% of users could not access the platform.
- **Root Cause:** A misconfigured Nginx server prevented the application from serving requests properly.

---

## **Timeline**
- **02:30 AM** - Monitoring system detected increased server error rates.
- **02:35 AM** - First alert received via automated monitoring.
- **02:40 AM** - Engineering team notified.
- **02:50 AM** - Initial assumption: database failure.
- **03:10 AM** - Checked database logs, found no issues.
- **03:30 AM** - Debugged API, identified Nginx misconfiguration.
- **04:00 AM** - Configuration corrected; server restarted.
- **05:45 AM** - Full functionality restored.

---

## **Root Cause and Resolution**
### **Root Cause**
The Nginx configuration file contained an incorrect **proxy_pass** directive, which caused the server to route traffic incorrectly. This misconfiguration resulted in all incoming requests failing.

### **Resolution**
- Identified the misconfiguration in the Nginx configuration file.
- Corrected the **proxy_pass** directive.
- Restarted the Nginx service.
- Verified that the API and web services were responding correctly.

---

## **Corrective and Preventative Measures**
### **Improvements Needed**
- Implement stricter CI/CD validation for configuration changes.
- Enhance monitoring alerts to detect misconfigurations earlier.
- Improve team response time to critical alerts.

### **Action Items**
- ✅ Add automated testing for Nginx configurations before deployment.
- ✅ Implement additional API endpoint health checks.
- ✅ Train engineers on troubleshooting Nginx-related issues.
- ✅ Configure failover servers to minimize downtime in future incidents.

---

### **Conclusion**
This incident highlighted the need for better configuration validation and faster debugging processes. The implemented fixes and preventive measures will help ensure similar issues do not occur in the future.

