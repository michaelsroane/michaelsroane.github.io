---
title: Sample Guide (Concepts and Procedures)
permalink: /how_to_example/
layout: single
author_profile: true
toc: true
---

**Note**: This is an example of documentation I have created for multiple organizations in the past. All product names, features, and bugs have been changed. I have changed or removed some content to obscure the organization, product, and release contents.

---

# Using the ProductAgent with ProductSecurity
ProductAgent sends endpoint data to ProductSecurity for analysis through either a proxy connection (traffic monitoring through the ProductSecurity proxy) or a direct connection (traffic monitoring directly through the Internet). This implementation requires licenses for both ProductAgent and ProductSecurity.

## About ProductAgent for ProductSecurity
ProductAgent provides security and monitoring of web activities through ProductSecurity. ProductAgent replaces the legacy SecurityAgent, which only supported proxy connections. 

## Migrating from SecurityAgent to ProductAgent
If your organization deploys SecurityAgent, follow this checklist to migrate from the legacy SecurityAgent to the new ProductAgent.

1. Uninstall SecurityAgent from the endpoint.
2. Restart the endpoint.
3. Download the ProductAgent installation package. See the "Download ProductAgent from the ProductSecurity Console" procedure below.
4. Install ProductAgent on the endpoint. See the "Install ProductAgent on a Windows Endpoint" procedure below.

## Download ProductAgent from the ProductSecurity Console
Download the ProductAgent installation package from the ProductSecurity Console:
1. Sign into the ProductSecurity Console.
2. Go to **Security > Settings > Endpoint**.
3. On the **Downloads** tab, select **ProductAgent for Windows**.
4. Click the download link.

## Install ProductAgent on Windows Endpoints
Use Microsoft Endpoint Configuration Manager to install ProductAgent on your endpoints.

Before you begin: 
- Download the ProductAgent installation package
- Install .Net Framework 4.6.1

1. In Microsoft Endpoint Configuration Manager, open the **Software Library**, then go to **Application
Management > Application**.
2. Right-click and select **Create Application**. 
3. The **Create Application Wizard** displays. Complete the following:
   1. On the **General Information** tab, enter the **Name** and additional fields,
such as **Publisher** and **Administrator name**, then click **Next**.
   2. On the **Software Center** tab, click **Edit** next to **User Categories**.
   3. On the **User Categories** dialog box, select the **Security** check box, then click **OK**.
   4. On the **Software Center** tab, click **Next**.
   5. On the **Deployment Types** tab, click **Add**. 
4. The **Create Deployment Type Wizard** displays. Complete the following:
   1. On the **General** tab, select **Script Installer** for the **Type**, select **Manually specify the deployment type information**, then click **Next**.
   2. On the **General Information** tab, enter the name and additional information, then click **Next**.
   3. On the **Content** tab, browse to the location of the ProductAgent installation package, specify the
command used to install ProductAgent (`"C:\Program Files (x86)\<mycompany>\Installer.exe" -x`),
and browse to the location of the ProductAgent uninstallation package. Click **Next**.
   4. On the **Detection Method** tab, click **Add Clause**.
   5. Use the **Detection Rule** dialog box to add a rule to detect the presence of the ProductAgent installation. Click **OK**.
   6. On the **Detection Method** tab, click **Next**.
   7. On the **User Experience** tab, select the following:
      - **Installation behavior** = **Install for system**
      - **Logon requirement** = **Whether or not a user is logged on**
      - **Installation program** = **visibility Hidden**
      - **Maximum run time** = **15 minutes**
      - **Estimated installation time** = **1 minute**
      then click **Next**.
   8. On the **Requirements** tab, there are no requirements. Click **Next**.
   9. On the **Dependencies** tab, there are no dependencies. Click **Next**.
   10. On the **Summary tab**, review the information, then click **Next**.
   11. On the **Completion** tab, click **Close**. The Create Deployment Type Wizard closes.
5. On the **Deployment Types** tab of the Create Application Wizard, click **Next**.
6. On the **Summary** tab, review the information, then click Next.
7. On the **Completion** tab, click **Close**. The Create Application Wizard closes.
8. Return to the Microsoft Endpoint Configuration Manager, open the **Software Library**, then go to **Application Management > Application**.
9. Right-click the application you created, then click **Deploy**. The **Deploy Software Wizard** displays.
   1. On the **General** tab of the Deploy Software Wizard, from the **Collection** option, click **Browse** and select the users and groups to deploy ProductAgent to, then click **OK**.
   2. On the **General** tab, click **Next**.
   3. On the **Content** tab, click **Add** and enter the distribution point.
   4. On the **Deployment Settings** tab, select the Action **Install** and the Purpose **Required**, then configure
additional settings as needed. Click **Next**.
   5. On the **Scheduling** tab, select **As soon as possible after the available time**, then click **Next**.
   6. On the **User Experience** tab, select **Hide in Software Center and all notifications**, then click **Next**.
   7. On the **Alerts** tab, click **Next**.
   8. On the **Summary** tab, review the information, then click **Next**.
   9. On the **Completion** tab, click **Close**. The Deploy Software Wizard closes.
10. View the deployment status at the bottom left-hand side of the Microsoft Endpoint Configuration Manager.

## Configure the ProductAgent Connection Mode in the ProductSecurity Console
Configure the ProductAgent connection mode in the ProductSecurity Console. There are three options: proxy connect, direct connect, and auto-switch.
- **Proxy connect** mode: When ProductAgent is in proxy connect mode, ProductAgent redirects web traffic through the cloud proxy to the Internet. If the connection to the cloud proxy is unavailable, then Endpoint Agent falls back to the configured Fallback mode.
- **Direct connect** mode: When ProductAgent is in direct connect mode, ProductAgent does not redirect web traffic through the cloud proxy. All web traffic connects to the Internet directly. ProductAgent connects to a disposition server to receive web policies. If the connection to the disposition server is unavailable, then ProductAgent falls back to the configured Fallback mode.
- **Auto-switch** mode: When ProductAgent is in auto-switch mode, ProductAgent starts in proxy connect mode and redirects web traffic through the cloud proxy to the Internet. ProductAgent switches to direct connect mode if:
 - Connectivity to the cloud proxy is lost.
 - Proxy connection performance is degraded. ProductAgent checks the connection latency performance every 30 minutes and compares the speed of the proxy connection and the direct connection. If the proxy connection is 3 times slower than the direct connection, ProductAgent switches to direct connect mode. When the proxy connection performance is no longer 3 times slower, ProductAgent switches back to proxy connect mode.
 ProductAgent switches back to proxy connect mode if:
 - Connectivity to the cloud proxy is restored.
 - Proxy connection performance improves. ProductAgent checks the connection latency performance every 30 minutes and compares the speed of the proxy connection and the direct connection. When the proxy connection performance is no longer 3 times slower, ProductAgent switches back to proxy connect mode.
 If the connections to both the cloud proxy and disposition server are unavailable, then ProductAgent falls back to the configured Fallback mode.

### Configuring the ProductAgent Connection Mode
Follow this procedure to set the ProductAgent connection mode in the ProductSecurity Console.

The connection mode is configured in the web policy in the ProductSecurity Console. The connection mode is set per policy and different policies can have different connection modes. 

1. Sign into the ProductSecurity Console.
2. Go to **Security > Policy Management > Policies**.
3. In the **Policies** section, click a **Policy Name** to edit the policy.
4. Go to the **Endpoints** tab.
5.  Under **Endpoint Configuration**, select the connection mode:
 - **Auto-switch** (recommended): ProductAgent starts in proxy connect mode and web traffic is redirected through the cloud proxy to the Internet. When the connection to the cloud proxy is unavailable, ProductAgent switches to direct connect mode. When the cloud proxy is available again, ProductAgent returns to proxy connect mode.
 - **Proxy Connect**: When ProductAgent is in proxy connect mode, ProductAgent redirects web traffic through the cloud proxy to the Internet. If the connection to the cloud proxy is unavailable, then Endpoint Agent falls back to the configured Fallback mode.
 - **Direct Connect**: When ProductAgent is in direct connect mode, ProductAgent does not redirect web traffic through the cloud proxy. All web traffic connects to the Internet directly. ProductAgent connects to a disposition server to receive web policies. If the connection to the disposition server is unavailable, then ProductAgent falls back to the configured Fallback mode.
6. Click **Save**.

Next steps
Select the fallback mode for the connection.

### Configuring the ProductAgent Fallback Mode
The fallback mode is used when ProductAgent cannot connect to either the cloud proxy for the proxy connect mode or the disposition server for the direct connect mode.

The fallback mode is configured in the web policy in the ProductSecurity Console. The connection mode is set per policy and different policies can have different connection modes. 

1. Sign into the ProductSecurity Console.
2. Go to **Security > Policy Management > Policies**.
3. In the **Policies** section, click a **Policy Name** to edit the policy.
4. Go to the **Endpoints** tab.
5. Under **Endpoint Configuration**, select the fallback mode:
   - **Open**: Web traffic bypasses ProductAgent and goes directly to the Internet. In Open fallback mode, ProductAgent is not providing any monitoring or protection of your organization’s web traffic. All attempts to access the Internet are allowed.
   - **Closed**: ProductAgent stops all web traffic from accessing the Internet. All attempts to access the Internet are blocked.
   - **Safe**: ProductAgent blocks or allows web traffic based on web policies cached on the local endpoint. This option is not available if the connection mode is set to Proxy Connect.
6) Click **Save**.
