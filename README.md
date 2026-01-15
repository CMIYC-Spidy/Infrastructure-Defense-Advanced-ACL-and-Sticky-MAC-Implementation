<h1 align="center">Infrastructure Defense: Advanced ACL & Sticky MAC Implementation</h1>

<div style="background-color: #1e1e1e; padding: 15px; border-radius: 5px; border-left: 5px solid #007acc;">
  <strong>Tool Used:</strong>
  <ul>
    <li><a href="https://www.netacad.com/cisco-packet-tracer"> Cisco Packet Tracer </li>
  </ul>
</div>
      
<h2>Objective</h2>

<p>To design and implement a secure corporate network using a Star Topology that enforces departmental isolation through Layer 3 Access Control Lists (ACLs) and protects physical hardware through Layer 2 Port Security.</p>

<img width="98%" height="98%" alt="Screenshot 2026-01-15 132752" src="https://github.com/user-attachments/assets/85ed5513-708b-4cbe-aecb-f51651a101af" />

<h2>Security Policy 1: Departmental Isolation (Layer 3)</h2>

<p>The network is segmented into three VLANs: HR (10), IT (20), and Sales (30). I configured Extended ACLs on the Router to ensure:</p>

<ul>
  <li><b>Administrative Authority:</b> The IT department has unrestricted access to all segments for management and troubleshooting.</li>
  <li><b>Zero Trust Between Departments:</b> HR and Sales are strictly prohibited from communicating with each other to protect sensitive data.</li>
</ul>
<p align="center">
<img width="98%" height="98%" alt="Screenshot 2026-01-15 134938" src="https://github.com/user-attachments/assets/26ae179b-f6d3-44ec-95dc-f67946d9bba7" />
<br />
<br />
</p>
<ul>
  <li><b>Result:</b> Unauthorized pings fail immediately with a "Destination Host Unreachable" response. This proves the Router is actively filtering traffic based on the specific security policy.</li>
</ul>

<p align="center">
<img width="98%" height="98%" alt="Screenshot 2026-01-15 135600" src="https://github.com/user-attachments/assets/eabb65f1-9a8a-4fb4-8701-ccc3e422138d" />
<br />
<br />
<img width="98%" height="98%" alt="Screenshot 2026-01-15 140010" src="https://github.com/user-attachments/assets/2e2bf0ea-4664-4313-a3d2-2ca432316fb0" />
</p>

<h2>Security Policy 2: Hardware Lockdown (Layer 2)</h2>

<p>To prevent unauthorized physical access, such as MAC Spoofing or unauthorized device swapping, I implemented Port Security on all access switches.</p>

<ul>
  <li><b>Sticky MAC Learning:</b> Switches are configured to learn and "stick" to the first hardware address connected to each port, preventing unauthorized devices from ever gaining a link.</li>
</ul>

<p align="center">
<img width="1365" height="720" alt="Screenshot 2026-01-15 141020" src="https://github.com/user-attachments/assets/81718a35-c358-4961-b4fd-baabfa35d6eb" />
<br />
<br />
</p>

<ul>
  <li><b>Automatic Shutdown:</b> If an unknown device is plugged into a secure port, the switch triggers a violation and puts the port into an <code>err-disabled</code> state.</li>
  <li><b>Result:</b> This ensures that even with physical access to the building, an attacker cannot join the network without a manual reset by an IT administrator.</li>
</ul>

<p align="center">
<img width="98%" height="98%" alt="Screenshot 2026-01-15 143232" src="https://github.com/user-attachments/assets/2b4fc04d-40a9-41c9-b045-583f5e1a17f3" />
<br />
<br />
<img width="1363" height="720" alt="Screenshot 2026-01-15 143510" src="https://github.com/user-attachments/assets/45a6d160-e850-4ae6-8efb-9cfe01a297dc" />
<br />
</p>

<h2>Technical Skills Demonstrated</h2>

<ul>
  <li><b>Network Design:</b> Star Topology with Inter-VLAN Routing.</li>
  <li><b>Cybersecurity:</b> Extended ACL configuration and Traffic Filtering.</li>
  <li><b>Infrastructure Defense:</b> Layer 2 Port Security and MAC Filtering.</li>
</ul>

<h1>Final Reflection</h1>

Building this multi-layered security architecture provided me with a deep, hands-on understanding of how physical hardware defense and logical segmentation must align to create a resilient system. My biggest takeaway was the critical importance of configuration discipline; I learned that even a perfectly designed security policy can fail due to minor synchronization issues or incomplete port mapping across the access switches.

This project reinforced my ability to diagnose complex failures—such as identifying when a lack of Layer 3 traffic prevents a Layer 2 security violation from triggering—by isolating variables and using "known-good" reference points to find the root cause. By successfully implementing Inter-VLAN ACLs and Sticky MAC lockdown, I gained practical experience in managing traffic flow between isolated departments while maintaining the integrity of the overall infrastructure. Ultimately, this process taught me that building a secure system requires not just technical knowledge, but the persistence to troubleshoot through simulation nuances and protocol timings until a professional-grade defense is achieved.

Thank you for taking the time to review my project and for your consideration of my work.
