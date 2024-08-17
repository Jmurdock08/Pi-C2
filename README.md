Pi-C2

Self Hosted CloudC2 on Raspberry Pi for your HAK5 devices to connect to!
This will not run without a license from HAK5. You can get the community edition for free at 
https://shop.hak5.org/products/c2#c2-versions

***To validate the license the Pi must be connected to the internet!!!***

```wget -q https://c2.hak5.org/download/latest -O cloudc2.zip```
![wget](https://github.com/user-attachments/assets/e7bfc623-f58c-4e9b-af1c-c00e91594ca0)

```mkdir cloudc2```

```mv cloudc2.zip cloudc2```

```cd cloudc2```

```unzip cloudc2.zip```

![mkdir](https://github.com/user-attachments/assets/68a01e05-5b97-4e3f-a09e-ca89b80d8f36)

Run cloud c2

```./c2-3.4.0_armv8_linux -hostname 10.72.6.10```

![initial run](https://github.com/user-attachments/assets/10704980-9a2a-4d0f-9978-0498982589e4)

This will create your c2.db file. If you change Hostnames you will need to rerun this command 
and copy the new c2.db file in the location shown in the following steps!
ie: when we move this from a private ip to a public ip.

Now we are going to set up the c2 so it starts as a service whenever the device powers on!

```sudo mv c2-3.4.0_armv8_linux /usr/local/bin```

```sudo mkdir /var/cloudc2```

```sudo mv c2.db /var/cloudc2```

![systemprep](https://github.com/user-attachments/assets/bd69c2f1-2e1b-4193-8df0-ac9bfab9615a)

Now we will need to create a service file for C2.
NOTE: If you change the hostname from an private IP to a public you will need to edit this file as well!

```sudo nano /etc/systemd/system/cloudc2.service```

![c2service file](https://github.com/user-attachments/assets/b80d7aee-1c3b-43b8-995d-c9df77962824)

Now hit ctrl x, y, and finally enter.

Now we need to reload the systemctl daemon, Enable the services on boot, start the service and check the status of the service!

```sudo systemctl daemon-reload```

```sudo systemctl enable cloudc2.service```

```sudo systemctl start cloudc2.service```

![servicestart](https://github.com/user-attachments/assets/a775e018-5f1e-4c9b-ac70-3d8ddf5294f7)

```sudo systemctl status cloudc2.service```

![servicestatus](https://github.com/user-attachments/assets/feb5c4ac-37a4-421e-8be9-3b50c95d7374)

Now we must validate our c2 instance by entering the appropriate token (This was created the first time we ran our c2 instance.  The tokens are located where the grey boxes are in the picture above.) and license (You should receive this in your email from HAK5)

![c2tokensetup](https://github.com/user-attachments/assets/a5a1a9bc-266a-46ab-bd7d-6a775760fa3c)

If you are running this internally in your homelab theres no need to continue past this point. However if you want to be able to access it from anywhere in the world continue!
