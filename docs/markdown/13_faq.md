# FAQ
"_Have you tried turning it off and on again?_" 
 
As in any software, things sometimes do not go as planned. 
Which is probably teh reason you find yourself here.



##### Where is my Scarif Hub?
 
First check if the hub icon is not showing in your task bar. If it is not
go to the "scarif core environment", to the scripts folder and execute "scservice.exe".
This should start the the hub and all necessary background processes.


If it is still not staring go to the [Scarif Install Directory](./02_installation.md) into the tmp folder
and delete the ``.block_services`` file if it exists.



##### My Scarif Hub is missing some submenus?

If you create new application configuratens or add some extensions, the hub might not imidiatly update. You can 
manualy trigger an update using the "Update" button inside the hub.



##### Wrong team password!

 If for some reason your Scarif applications don't start and raise an password error try to delete
 the ``tmp`` folder inside the [Scarif Install Directory](./02_installation.md)
 

##### The Scarif tools do not show up in my DCC!

This can have multiple reasons:
 - Scarif Maya extension is not installed or not assigned in the Application Manager.
 - ``PATH`` or ``PYTHONPATH`` is not configured correctly and Scarif uses incompatible packages from other environments.