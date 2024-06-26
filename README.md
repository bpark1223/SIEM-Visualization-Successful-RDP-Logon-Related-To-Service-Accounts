<h1> SIEM-Visualization-Successful-RDP-Logon-Related-To-Service-Accounts <h1>
<h2>Description</h2>
In this project, I will create a SIEM visualization that monitors successful RDP logons related to service accounts. Remote Desktop Protocol (RDP) is a Microsoft-developed protocol that allows users to remotely access another computer's desktop environment over a network connection. Service accounts have high privileges, and their credentials are usually never used for RDP logons; therefore, it is important to monitor how they are used. In this example,  all service accounts on the environment start with svc-.
<br />

<h2>Languages and Utilities Used</h2>
- <b>VirtualBox</p>
- <b>Elastic</b>
<h2>Environments Used </h2>
- <b>Windows 10</b> 
<h2>Project walk-through:</h2>
</p> 1. After logging into Elastic, I click "edit" for the dashboard titled "SOC-alerts"
<img width="1423" alt="Screenshot 2024-06-26 at 12 55 52 PM" src="https://github.com/bpark1223/SIEM-Visualization-Successful-RDP-Logon-Related-To-Service-Accounts/assets/77799235/14692955-9bc3-40b3-9a67-ba58370c77ae">
</p> 2. I click "create visualization" after which I will be able to customize my settings and filter
<img width="1428" alt="Screenshot 2024-06-26 at 1 04 26 PM" src="https://github.com/bpark1223/SIEM-Visualization-Successful-RDP-Logon-Related-To-Service-Accounts/assets/77799235/25cab8a8-d348-4b4f-9b2d-f731d156c6b4">
</p> 3. To display accounts that were successfully logged on, I add a filter to consider event IDs that match Windows event code 4624 </p>
<img width="1418" alt="Screenshot 2024-06-26 at 2 22 37 PM" src="https://github.com/bpark1223/SIEM-Visualization-Successful-RDP-Logon-Related-To-Service-Accounts/assets/77799235/16818b23-d440-4a21-b133-52350c7a5e64">
</p> 4. Also, I need to add a filter to consider the log on type. In this case, it would be remote interactive. Therefore, winlog.logon.type is RemoteInteractive </p>
<img width="1427" alt="Screenshot 2024-06-26 at 2 25 59 PM" src="https://github.com/bpark1223/SIEM-Visualization-Successful-RDP-Logon-Related-To-Service-Accounts/assets/77799235/bad814ae-b6aa-49c3-8020-cea639899389">
</p> 5. I specify the type of visualization I want to create, which is "table". I then proceed to click "rows" to choose the specific elements that I want to include in the table. </p>
<img width="1421" alt="Screenshot 2024-06-26 at 2 29 47 PM" src="https://github.com/bpark1223/SIEM-Visualization-Successful-RDP-Logon-Related-To-Service-Accounts/assets/77799235/b9e4eeb3-78d1-414f-99c5-ff3eda8f41c9">
</p> 6. I configure the rows settings as follows: </p>
<img width="339" alt="Screenshot 2024-06-26 at 2 33 06 PM" src="https://github.com/bpark1223/SIEM-Visualization-Successful-RDP-Logon-Related-To-Service-Accounts/assets/77799235/13e5db2b-0392-439b-9a64-bb08e728bf00">
</p> 7. In the "metrics" window, I select "count"
<img width="1434" alt="Screenshot 2024-06-26 at 2 36 07 PM" src="https://github.com/bpark1223/SIEM-Visualization-Successful-RDP-Logon-Related-To-Service-Accounts/assets/77799235/cc1acb31-d22d-460f-997f-22c0a2332610">
</p> 8. I add two more rows to show where the successful RDP logon attempt occurred (host.hostname.keyword) and the machine that initiated the successful RDP logon attempt (related.ip.keyword).  </p>
<img width="348" alt="Screenshot 2024-06-26 at 2 41 14 PM" src="https://github.com/bpark1223/SIEM-Visualization-Successful-RDP-Logon-Related-To-Service-Accounts/assets/77799235/a7460311-ade2-402a-a60e-22f79363ca48">
<img width="345" alt="Screenshot 2024-06-26 at 2 44 05 PM" src="https://github.com/bpark1223/SIEM-Visualization-Successful-RDP-Logon-Related-To-Service-Accounts/assets/77799235/ec07b0a1-dfa9-41f8-9fe5-cc044b4c0054">
</p> 9. I want to monitor successful RDP logons  related to service accounts, knowing that all service accounts of the environment start with svc-. So, to conclude the visualization I need to specify the following KQL query: user.name: svc-*</p>
<img width="1431" alt="Screenshot 2024-06-26 at 2 51 29 PM" src="https://github.com/bpark1223/SIEM-Visualization-Successful-RDP-Logon-Related-To-Service-Accounts/assets/77799235/b39d7ea5-1ae8-4e65-b4c1-fe331431eb27">
</p> 10. Now I can see four columns with the following information: </p>
</p> -The service account whose credentials generated the successful RDP logon attempt event. </p>
   </p> -The machine on which the logon attempt occurred.</p>
</p> -The IP of the machine that initiated the logon attempt.</p>
</p> -The number of times the event has occurred. </p>
<img width="1421" alt="Screenshot 2024-06-26 at 2 54 19 PM" src="https://github.com/bpark1223/SIEM-Visualization-Successful-RDP-Logon-Related-To-Service-Accounts/assets/77799235/1cbb9a12-ed1f-4627-b829-0976b064a3d6">












