#Database Overview

This site contains a Z-Wave device database - this stores the configuration of a number of Z-Wave devices so that users can review the configuration, and it is available for export to open source Z-Wave software.  This database has been produced with openHAB in mind since I maintain the ZWave binding, although it's use is not limited to openHAB and I've produced an Open Z-Wave export as well.

A database of device information is required for Z-Wave since there is no way to know the devices configuration directly from the device. Some Z-Wave command classes have preset configuration, and these we can implicitly configure, however the configuration command class has no device specific declarations. This data is normally provided by the device manufacturer in the manual, or on their website.

A second reason for requiring this information is to allow us to present the device name to the user. Each device provides severable bits of information that allow software to detect what it is. These are the manufacturer ID, device ID, and device type. Additionally, the firmware version is also important for some devices as the parameters change between versions.

Finally, the device database allows software providers to make a note of non-standard behaviour of a device such that the software can continue to work properly with the device. This 'non standard behaviour' could be a non response to particular requests, or adding a command class that the device doesn't report during the discovery phase - a number of issues can be worked around in this way, and the use of the database allows this to be done in a common, and portable way.

The live version of the database can be found at [cd-jackson.com](http://www.cd-jackson.com/index.php/zwave/zwave-device-database)

#openHAB

As mentioned above, the database is largely about devices, and therefore isn't dependant on any particular software implementation. However, one of the drivers behind producing the database is to support openHAB, and there are a few issues that need to be addressed -: 

With the current XML based database, while not overly difficult, producing the XML files takes some knowledge. Therefore, maintaining the database is often left to a small group of people and updates are often left until this group have the time to create the files. The database here aims to solve this by providing a GUI to make it easy enough for anyone to enter and update records.
With the advent of openHAB-2, we now need to maintain two different database formats while openHAB-1 is still in use. This will take double the time to maintain, and will inevitably mean that differences will creep in, and errors will be made. Having a common data source is therefore highly desirable.
I'm often left searching the net for device manuals - the database provides a central location where I can store this data, and can therefore find it all easily again.
To improve the quality, having automatic data processing, and WYSIWYG editors to edit descriptions is a must! The more people who can update the database, the better quality it should become.
 

#Data Concept

The concept is to split information into individual fields - even if openHAB doesn't use fields of this name. This ensures that we can consolidate the data and present it in a consistent way. For each form (data type) there are a number of fields. Most are specific to the data, however some common description fields are provided. The following is the concept for their use -:

Label: This should be kept very short so that it renders nicely in all user interfaces. It should provide the name. This is text only.
Description: This should be a one line explanation of the field. This is text only.
Overview: This can be used to provide more detailed information on the field. Basic HTML is permitted in this field.
When generating the output files (eg the openHAB database XML files), a combination of these fields will be used to produce a consistent feel to the data. For example, when producing user interface help information for a parameter, data from the parameter, and the parameter options will be used to generate the user interface.

 

#Data Use

The data in this database is for free use. If you add data to the database, you acknowledge that it can be used for any purpose, commercial or not. Likewise, if you use the data from the database in your own product, you acknowledge that it is from an open source and may contain errors.