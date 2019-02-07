# Powershell-PrinterInstallGUI
This is a script made entirely to allow the remote install of Printer's, Drivers, and ports on multiple servers.

<#
Created by Benjamin Knight.
Version created on 2/4/2019 for Physicians Primary Care.

You can copy this code to your own script, either open it by running through powershell, or open it in the IDE and run it from there.

Desired additions or changes in order of time thought of:

Adding Property changes. Such as removing an installed tray or changing which tray is printed to. IE Tray 2 instead of auto select. At the moment it seems the the M608 driver does not allow this.

Add Rename function using:

$Printer = get-printer -Name "" -ComputerName ""

rename-printer -InputObject $Printer -NewName ""

#>

<#
Completed Work:

8/18

ProgressBar function has been added. Requires the function be called while nested in the foreach loop and the variable $P++ added after the actions have taken place. 
(++ causes the variable to increment upward -- does so in reverse)
Added an error message after not knowing why the script didn't do anything on a single server. 
Since most problems would be due to the driver not being installed I've just added the error to state the driver isn't installed.
Added Tabs to main window, this will allow me to add more due to having more space to work with.
Changed the function for Port adding to also house adding a printer.
Added Port textbox so the port name has to be added now and not just assumed to be the same name as the printer name.
Added removal options tab to house Remove Printer and Remove Port. May later add Driver Removal as well.

9/18

Added Permissions changes under the Edit Printer Settings Tab
Added Printerpermissions Function

10/18

Added Clear console button to make a cleaner output when needed
Completed work on allowing either just the driver to be changed or just the comment to be changed.
Revamped the tabs, moved adding Port and Printer to their own tab and removed the file options.
Added the functions to add and remove drivers as well as a button to browse for the .inf
Redid most of the variables adding either the "Edit" or "AddOrRemove" prefix to make it more clear of what they do.

11/18
Revamped most of the error messages to better point to the problem.
Added Location field per request.
Added messages for performing tasks on one server at a time, due to the progress bar not making the completion of a task clear for only one server.
Changed the way the progress bar looks, BarAction will make it more detailed.

#>
