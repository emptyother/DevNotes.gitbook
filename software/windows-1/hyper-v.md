# Hyper-V troubleshooting

## Hyper-V cannot connect to the internet

### Using Your Windows 8 Wireless Connection Inside Hyper-V

As a Microsoft developer, I prefer to leverage Microsoft tools whenever possible, thus, I was ecstatic to hear about Hyper-V support in Windows 8 Professional. It is by far one of the most exciting features in the new operating system. Traditionally, I have leveraged VMWare player from my laptop to compartmentalize my client development environments. I have found that dedicating a VM to each client keeps my laptop clean and reduces overhead of all the various applications we need as developers. Recently, I embarked to setup a new Hyper-V VM on Windows 8 and discovered that Hyper-V does not automatically create a wireless adapter with the guest VM. So, despite having a Wi-Fi connection on my laptop, my new VM could not access the Internet. After some research and tinkering, I was able to configure Hyper-V to use my laptop’s wireless connection. I thought it would be helpful to document the process as a way to help others looking to switch to Windows 8’s Hyper-V. The Hyper-V Virtual Switch is a software-based layer-2 network switch built into Windows 8’s Hyper-V Manager. The switch allows you to connect virtual machines to virtual or physical networks. In this case, we will be setting up an internal virtual network adapter to support communication between the laptop running Windows 8 and the VM running Windows Server 2012.

1. Launch Hyper-V Manager from your App Menu
2. In the Actions area in right-hand navigation, click “Virtual Switch Manager”
3. When the Virtual Switch Manager window opens, select “New virtual network switch” on the left, select “Internal” on the right, and then click the “Create Virtual Switch” button
4. Give the new switch a name like “Virtual WLAN” and click “OK”
5. In Windows 8 sys tray, right-click on the wireless icon and click on “Open Network and Sharing Center.” You will see the new Unidentified Network connected to the vEthernet \(Virtual WLAN\) adapter.
6. Back in Hyper-V Manager, select your VM \(make sure it is turned off\) and on the lower left side, click “Settings”
7. The Settings window will default to Add New Hardware, select “Legacy Network Adapter” and click “Add”
8. In the Legacy Adapter details, select the “Virtual WLAN” adapter we configured earlier and click “OK”
9. Go back to Windows 8’s Network and Sharing Center and click on the “Wi-Fi” link \(or the name of your laptop’s wireless adapter\) listed in the Connections
10. In the adapter status window, click “Properties”
11. In the Properties window, click the Sharing tab, check the “Allow other network users…” box, select “vEthernet \(Virtual WLAN\)” \(or the name of your wireless adapter\), and click “OK” to close the window
12. Click Close to exit the Wi-Fi status window
13. To confirm you have it setup correctly, click on the “Change adapter settings” link. You should see the word Shared beside your wireless connection.

Now, whether you are trying to get some work done at the airport or giving a demo at the client’s office, your Hyper-V VM can share your laptop’s wireless connection.

**Source**: [http://blog.credera.com/technology-insights/microsoft-solutions/using-your-windows-8-wireless-connection-inside-hyper-v/](http://blog.credera.com/technology-insights/microsoft-solutions/using-your-windows-8-wireless-connection-inside-hyper-v/)

