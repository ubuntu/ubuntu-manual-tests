Scope of this test is to verify that the system is installed in itself starting from the setting hostname step. **WARNING This test uses pre-selected answers to installation questions (the preseed file). The preseed in use will unilaterally allocate the whole hard drive for the install. This will cause the complete loss of any data then in the hard drive. We strongly recommend you to use a 'trash and burn' system -- i.e., a system you do not mind losing the contents of the hard drive(s). Virtual machines are also a good option (and a nice helper to boot an Ubuntu ISO is testdrive). It is also a good idea to disconnect any external hard drive(s) you do not want to participate in the reformatting. On a trash and burn server, boot the Ubuntu Server ISO (or, for VMs, run testdrive, and select either an i386 or an amd64 server image -- should be options 2 or 7).** _Proceed in your native language if you wish. Instructions will remain in English_

Boot up the image
Choose the desired language, press F6, Esc, and F8. This will show you the Boot Options line: Boot Options file=/cdrom/preseed/ubuntu-server.seed vga=788 initrd=/install/initrd.gz quiet --
Replace 'file=/cdrom/preseed/ubuntu-server.seed' by 'auto url=http://people.canonical.com/~plars/default.cfg auto=true priority=critical'. The Boot Options line should now look like: Boot Options auto url=http://people.canonical.com/~plars/default.cfg auto=true priority=critical vga=788 initrd=/install/initrd.gz quiet --
Press Enter to accept the boot command line and start the installation
From this point on, the installation should proceed automatically. Wait until the system reboots. 
At the login insert ubuntu as userid and **ubuntu** as password
Verify that the server is working executing:
    ntptime
    the output should look like: 
    
    
                    njin@quantic:~/Ubuntu$ ntptime
                    ntp_gettime() returns code 0 (OK)
                    time d3d92552.3858c000  Fri, Aug 17 2012 22:17:22.220, (.220104),
                    maximum error 4516 us, estimated error 16 us, TAI offset 0
                    ntp_adjtime() returns code 0 (OK)
                    modes 0x0 (),
                    offset 0.000 us, frequency 0.000 ppm, interval 1 s,
                    maximum error 4516 us, estimated error 16 us,
                    status 0x1 (PLL),
                    time constant 7, precision 1.000 us, tolerance 500 ppm,
                

**If all actions produce the expected results listed, please [submit](<>) a 'passed' result. If an action fails, or produces an unexpected result, please [submit](<>) a 'failed' result and [file a bug](<>). Please be sure to include the bug number when you [submit](<>) your result.**
