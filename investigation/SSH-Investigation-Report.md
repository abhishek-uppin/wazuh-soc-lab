# Wazuh Home Lab: SSH Investigation Report

## 1. Findings

Wazuh detected multiple failed login attempts against the monitored Ubuntu server and the source IP address was blocked by Wazuh Active Response.

- **Source IP:** `192.168.237.135`
- **Failed authentication attempts:** 3
- **Time range:** October 3, 2026, 18:51:05 – 18:51:11
- **Successful login:** None observed

---

## 2. Investigation Summary

The investigation began after Wazuh generated an alert for repeated SSH authentication failures.

---

## 3. WHO / WHAT / WHEN / WHERE / WHY / HOW

### WHO

- **Source IP:** `192.168.237.135`
- **Target IP:** `192.168.237.134`

### WHAT

Multiple failed SSH authentication attempts.

### WHEN

- **Timestamp:** October 3, 2026, 17:51:11.990
- **Timezone:** Irish Standard Time (GMT +1)

### WHERE

- **Source:** `192.168.237.135`
- **Destination:** `192.168.237.134`

### WHY

**Likely Credential Access**

### HOW

The source generated repeated SSH authentication attempts.

---

## 4. Evidence

The following Wazuh alert was observed during the investigation:

- **Alert:** Multiple SSH login failures observed from the same source IP
- **Rule ID:** `100101`
- **Timestamp:** October 3, 2026, 18:51:11.990
- **Source IP:** `192.168.237.135`
- **Target IP:** `192.168.237.134`
- **Username:** `zoro`

### Evidence Screenshot

<img width="1917" height="1092" alt="Screenshot 2026-10-02 171818" src="https://github.com/user-attachments/assets/d788ef5b-e4a8-4e7b-b416-8273a486de90" />

---

## 5. Impact Assessment

- Multiple SSH authentication attempts failed.
- No successful SSH login was observed.
- The source IP was blocked by Wazuh Active Response using `firewall-drop`.
- No confirmed compromise or unauthorized access was identified based on the investigated evidence.

---

## 6. Recommendations

- Restrict SSH access to trusted IPs, networks, and VPN only.
- Use strong, unique passwords for password-based SSH authentication.
- Use SSH key-based authentication instead of password-based authentication.
- Maintain and review Wazuh Active Response configuration to ensure automated blocking.

---

## 7. Analyst Conclusion

The investigation identified three failed SSH authentication attempts against the monitored Ubuntu server from source IP `192.168.237.135`.

Wazuh detected the repeated authentication failures and triggered the configured Active Response, which blocked the source IP using `firewall-drop`.

No successful SSH authentication or confirmed unauthorized access was observed during the investigation. Based on the available evidence, the activity was contained without a confirmed compromise of the monitored host.
