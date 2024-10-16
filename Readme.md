🌐 𝙐𝙣𝙡𝙤𝙘𝙠𝙞𝙣𝙜 𝙎𝙚𝙖𝙢𝙡𝙚𝙨𝙨 𝘾𝙤𝙣𝙣𝙚𝙘𝙩𝙞𝙫𝙞𝙩𝙮 𝙞𝙣 𝘼𝙒𝙎 𝙬𝙞𝙩𝙝 𝙑𝙋𝘾 𝙋𝙚𝙚𝙧𝙞𝙣𝙜 𝐰𝐢𝐭𝐡 𝐓𝐚𝐬𝐤𝐬🌐

🔗 𝗪𝗵𝗮𝘁 𝗶𝘀 𝗩𝗣𝗖 𝗣𝗲𝗲𝗿𝗶𝗻𝗴?
VPC Peering allows you to connect two Virtual Private Clouds (VPCs) securely, enabling resources in both VPCs to communicate using private IP addresses. Whether they reside in the same region or different ones, VPC Peering facilitates a seamless networking experience.

𝒕𝒚𝒑𝒆𝒔:
1. 𝒊𝒏𝒕𝒓𝒂-𝒓𝒆𝒈𝒊𝒐𝒏 𝒗𝒑𝒄 
it makes the connection between two VPC's inside of same account and same region.
2. 𝒊𝒏𝒕𝒆𝒓-𝒓𝒆𝒈𝒊𝒐𝒏 𝒗𝒑𝒄 𝒑𝒆𝒆𝒓𝒊𝒏𝒈.
it makes the connection between two VPC's inside of same account and different regions.
3. 𝑪𝒓𝒐𝒔𝒔-𝒂𝒄𝒄𝒐𝒖𝒏𝒕 𝒗𝒑𝒄 𝒑𝒆𝒆𝒓𝒊𝒏𝒈.
the name it self states that we can able to do make the connection between different VPC accounts.

# Scenario Overview of task:
In this **scenario**, we have **two VPCs** located in the **us-east-1** and **one VPC** in **us-east-2** regions. \
Each VPC utilizes multiple Availability Zones (AZs) to ensure high availability and fault tolerance.

## Architecture diagram:
![new](https://github.com/user-attachments/assets/b3ac07c2-d1f7-4279-880e-69a075d63d7e)

###############################################################################################


# Task 1:
✅ Create two VPCs in same region (different AZs) i.e \
✅ one for App server and second for Web Server. \
✅ Create an instance in each VPC. \
✅ Configure Route Tables for both app and web server. \
✅ Establish VPC peering between the App and web server VPCs. (intra-region VPC peering) \
✅ Verify connectivity between the instances in both VPCs.

# Task 2:
✅ Create another VPC in different region i.e for DB server \
✅ Create an instance in VPC. \
✅ Configure Route Tables for DB server. \
✅ Establish VPC peering between the DB and APP server VPCs. (inter-region VPC peering). \
✅ Verify connectivity between the instances in both VPCs. 

# Task 3:
✅ Establish VPC peering between the DB and WEB server VPCs. (inter-region VPC peering). \
✅ Verify connectivity between the instances in both VPCs. 


# Solution:

# Creating a VPC Peering Connection:
To establish a **VPC peering connection** between the \
App VPC (us-east-1) and Web VPC (us-east-1), \
App VPC (us-east-1) and DB VPC (us-east-2) , \
Web VPC (us-east-1) and DB VPC (us-east-2) \
follow these steps:

![image](https://github.com/user-attachments/assets/3cb5a7ab-34e2-4973-aae3-d654f5675ddf)


# Navigate to the VPC Dashboard:
•	Open the AWS Management Console. \
•	Select VPC from the Services menu.
# Create a Peering Connection:
•	In the left-hand navigation pane, click on Peering Connections. \
•	Click on Create Peering Connection.\
# Configure the Peering Connection:
•	Requester VPC: Select the VPC ID of the App VPC (which is requesting the peering). \
•	Accepter VPC: Specify the VPC ID of the Web VPC. \
•	If the VPCs are in different AWS accounts or regions, ensure the correct account and region are selected. \
•	Click Create Peering Connection.
# Accept the Peering Connection:
•	Navigate to the Accepter VPC (Web VPC). \
•	Find the pending request in Peering Connections. \
•	Select it and click on Actions > Accept Request to approve the peering connection.

![peering-connections](https://github.com/user-attachments/assets/1146f08b-18a4-43a7-87f5-397abccce01f)


# Update Route Tables:
•	Add **routes** in the route tables of VPCs, allowing traffic to pass between them. \
•	In **App VPC**, point the route table to the Web **VPC’s CIDR block (172.16.0.0/16)** and **DB VPC’s CIDR block (192.168.0.0/16)** \
•	In **Web VPC**, point the route table to the **App VPC’s CIDR block (10.0.0.0/16)** and **DB VPC’s CIDR block (192.168.0.0/16)** \
•	In **DB VPC**, point the route table to the **App VPC’s CIDR block (10.0.0.0/16)** and **WEB VPC’s CIDR block (172.16.0.0/16)**

![image](https://github.com/user-attachments/assets/7d8294fb-525f-4d16-bbb6-69cedfe35ae5)


# Security Group Rules:
•	Ensure the security groups of all instances allow traffic from the respective peered VPC.

# Final Note:
Once your peering connections and routing are in place, you’ll have seamless, private communication between the App, Web, and DB servers across regions.



# Now, you can test the connection between the
•	**App server and Web server**, \
•	**App server and DB server**, \
•	**Web server and DB server**, \
using the **private IP** of the servers. You should be able to ping or establish connection between them.

################################################################################################

![vpc-peering](https://github.com/user-attachments/assets/70ff435e-018d-469e-9376-f706216c6705)


















