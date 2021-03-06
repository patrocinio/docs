{:new_window: target="_blank"} 

# Getting started with {{site.data.keyword.blockstorageshort}} (Experimental)

{{site.data.keyword.blockstoragefull}} provides access to block level storage for transaction intensive workloads and runtimes in need of persistent storage.

You can use IBM {{site.data.keyword.blockstorageshort}} for {{site.data.keyword.Bluemix_notm}} to create block storage devices that can be attached to virtual machines. The data in block storage devices persists beyond the lifecycle of your virtual machines. IBM {{site.data.keyword.blockstorageshort}} uses OpenStack Cinder to manage the volume lifecycle.

Block storage volumes are created through an IBM {{site.data.keyword.blockstorageshort}} service instance. You can attach the volumes to a virtual machine under a particular device that you provide or the system can automatically select an available device name. The virtual machine performs its I/O operations directly with the specified device independent of the {{site.data.keyword.blockstorageshort}} service.

You can also create block-level snapshots of volumes. {{site.data.keyword.blockstorageshort}} service does not allow the creation of snapshots while the volume is attached, so the resulting snapshots will be crash-consistent. 

## How to create a {{site.data.keyword.blockstorageshort}} service instance
To create an instance of the {{site.data.keyword.blockstorageshort}} service in your space, follow these steps:
 
1.	Go to the **{{site.data.keyword.Bluemix_notm}}** Catalog tab and enter **{{site.data.keyword.blockstorageshort}}** into the search box, or go to **Services** and select **Storage**. Click the **{{site.data.keyword.blockstorageshort}}** service. 
2.	Enter a space and service name. Select a plan and click **Create**.
 	
The {{site.data.keyword.blockstorageshort}} service is only supported in an unbound context. 

An instance of {{site.data.keyword.blockstorageshort}} service is created in your space. You can open the {{site.data.keyword.blockstorageshort}} UI to manage volumes anytime by clicking the service instance icon.

## {{site.data.keyword.blockstorageshort}} user interface (UI)
The {{site.data.keyword.blockstorageshort}} graphical user interface provides a high-level overview of your storage volumes, snapshots, and total storage consumption for both volumes and snapshots at the top of the window. 

The header includes the date and time of the last UI refresh. You can use the refresh icon (a circular arrow icon) to refresh the UI manually, if needed. 

Use the search bar to find volumes based on the string that you enter. The tables are filtered as you type to show only the volumes that match the entered search string.

Below the overview are two tabs for volumes and snapshots. The volume tab is selected by default. The tables on this tab list detailed information about available and attached volumes. Each row in a table shows the most important properties of a volume. Additional properties are visible when you expand a row. Attached volumes also show the virtual machine instance and the device that the volume is attached to. 

The snapshot tab shows a table of snapshots with similar properties and behavior. 

Use the Create icon or the Actions drop-down list above the tables to create a new volume or to manipulate existing ones. 

## Volume actions

### Create a volume

1.	Click **Create** to start the **Create Volume** dialog.
2.	Provide the size of the volume that you want. Decimal numbers are not accepted. The size is limited by the quota that is assigned to your space.
3.	Provide a name. The name is not mandatory. It is for display purposes only.
4.	Optionally, provide a more detailed description of the volume. 
5.	Click **Create** to submit the information and close the dialog. 

Creating a volume can take a few moments. If the volume is not immediately visible in the table of available volumes, click the refresh icon (circular arrow icon) at the top of the page. 

### Delete a volume

1.	Select the volume that you want to delete.
2.	Click **Delete**.
3.	Confirm the deletion of this volume.

You cannot delete a volume that is attached to a virtual machine. You must detach the volume first.

### Extend a volume
You can increase the volume in size through the **Extend** action. You cannot reduce the size of a volume.

1.	Select the volume to be extended.
2.	Click **Extend**.
3.	Select the new size of the volume. Provide the new total size of the volume.
4.	Click **Extend** to submit the information and close the dialog. 

To be extended, a volume must be in **Available** state. 

### Attach and detach a volume to a virtual machine
Volumes are attached and detached from virtual machines as devices with a specific device name. For a virtual machine to be able to persist data on a volume, you must attach the volume to the virtual machine.

To attach a volume, follow these steps: 

1.	Select a volume from the list of available volumes.
2.	Click **Attach**.
3.	In the Attach dialog, select an instance of a virtual machine from the drop-down list. 
4.	Optionally, specify the device to be used to attach this volume. If you do not specify the device, the system automatically selects the first available device on the virtual machine.
5.	Click **Attach** to submit the information and close the dialog.

The volume is listed in the table of attached volumes with the information about the virtual machine instance. 
The virtual machine can now use the device with persistent data. 

To detach a volume, follow these steps: 

1.	Select a volume from the list of attached volumes. 
2.	Click **Detach**.
3.	Confirm the detachment in the dialog. 

After it is detached, the volume is no longer available for I/O operations in the virtual machine instance. In the {{site.data.keyword.blockstorageshort}} service UI, the volume is now available to be attached to other virtual machines.

## Snapshot actions

### Create a snapshot

1.	Select the **Volumes** tab to get a list of volumes.
2.	Select the volume that you want to create a snapshot of in the unattached volumes column. Make sure that the volume you select is unattached. The selected volume is highlighted. 
3.	Click **Actions** and select **Create Snapshot** from the drop-down list.
4.	Give the snapshot a name and click **Create**.

**Note:** You cannot delete a volume while snapshots for the volume exist. 

### Create a volume from a snapshot

1.	Select the **Snapshots** tab to get a list of snapshots.
2.	Select the snapshot that you want to create a volume from. The selected snapshot is highlighted.
3.	Click **Actions** and select **Create Volume** from the drop-down list.
4.	Give the new volume a name and optionally a new size and click **Create**. 

**Note:** The new volume size must be equal or greater than the snapshot size. 

### Delete a snapshot

1.	Select the **Snapshots** tab to get a list of snapshots.
2.	Select the snapshot that you want to delete. The selected snapshot is highlighted.
3.	Click **Actions** and select **Delete**. 



># Related Links {:class="linklist"}
>## API Reference {:id="api"}
>* [OpenStack Block Storage (Cinder) API v2](http://developer.openstack.org/api-ref-blockstorage-v2.html){: new_window}
>
>{:elementKind="article" id="rellinks"}
