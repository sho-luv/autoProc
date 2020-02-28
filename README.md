```
          ▄████████ ███    █▄      ███      ▄██████▄     ▄███████▄    ▄████████  ▄██████▄   ▄████████
         ███    ███ ███    ███ ▀█████████▄ ███    ███   ███    ███   ███    ███ ███    ███ ███    ███
         ███    ███ ███    ███    ▀███▀▀██ ███    ███   ███    ███   ███    ███ ███    ███ ███    █▀
         ███    ███ ███    ███     ███   ▀ ███    ███   ███    ███  ▄███▄▄▄▄██▀ ███    ███ ███
       ▀███████████ ███    ███     ███     ███    ███ ▀█████████▀  ▀▀███▀▀▀▀▀   ███    ███ ███
         ███    ███ ███    ███     ███     ███    ███   ███        ▀███████████ ███    ███ ███    █▄
         ███    ███ ███    ███     ███     ███    ███   ███          ███    ███ ███    ███ ███    ███
         ███    █▀  ████████▀     ▄████▀    ▀██████▀   ▄████▀        ███    ███  ▀██████▀  ████████▀
                                                                     ███    ███
```
<h4 align="center">Auto All The Procs</h4>
<p align="center">
  <a href="https://twitter.com/lydericlefebvre">
    <img src="https://img.shields.io/badge/Twitter-%40sho_luv-blue.svg">
  </a>
</p>

# autoProc.py

This tool uploads procdump64.exe to a windows box and dumps the lsass.exe memory.It then downloads the lsass dump and names it with the IP address it came from.
Once it is downloaded it runs pypykatz against the lsass.dmp file to extrate the cleartext passwords from the dump.

<img src="https://github.com/sho-luv/autoProc/blob/master/img/autoProc.gif" alt="autoProc" />

## How to Use
```
$ ./autoProc.py 
Impacket v0.9.21.dev1+20200210.172751.a0aca12c - Copyright 2020 SecureAuth Corporation

usage: autoProc.py [-h] [-share SHARE] [-nooutput] [-debug] [-codec CODEC]
                   [-hashes LMHASH:NTHASH] [-no-pass] [-k] [-aesKey hex key]
                   [-dc-ip ip address] [-A authfile]
                   target [command [command ...]]

Executes a semi-interactive shell using Windows Management Instrumentation.

positional arguments:
  target                [[domain/]username[:password]@]<targetName or address>
  command               command to execute at the target. If empty it will
                        launch a semi-interactive shell

optional arguments:
  -h, --help            show this help message and exit
  -share SHARE          share where the output will be grabbed from (default
                        ADMIN$)
  -nooutput             whether or not to print the output (no SMB connection
                        created)
  -debug                Turn DEBUG output ON
  -codec CODEC          Sets encoding used (codec) from the target's output
                        (default "UTF-8"). If errors are detected, run
                        chcp.com at the target, map the result with
                        https://docs.python.org/2.4/lib/standard-
                        encodings.html and then execute wmiexec.py again with
                        -codec and the corresponding codec

authentication:
  -hashes LMHASH:NTHASH
                        NTLM hashes, format is LMHASH:NTHASH
  -no-pass              don't ask for password (useful for -k)
  -k                    Use Kerberos authentication. Grabs credentials from
                        ccache file (KRB5CCNAME) based on target parameters.
                        If valid credentials cannot be found, it will use the
                        ones specified in the command line
  -aesKey hex key       AES key to use for Kerberos Authentication (128 or 256
                        bits)
  -dc-ip ip address     IP Address of the domain controller. If ommited it use
                        the domain part (FQDN) specified in the target
                        parameter
  -A authfile           smbclient/mount.cifs-style authentication file. See
                        smbclient man page's -A option.
```
