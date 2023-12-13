## netcat
Visual studio solution (updated for VS2022) for netcat (netcat-win32-1.12.zip)  
netcat source code was downloaded from https://eternallybored.org/misc/netcat/

### Available Solution Configurations
- Debug
- Debug (with -e Option)
- Debug Static
- Debug Static (with -e Option)
- Release
- Release (with -e Option)
- Release Static
- Release Static (with -e Option)

### -e Option notes
Configurations named "with -e Option" define the **GAPING_SECURITY_HOLE** constant when building the executable which enables the -e command line option.

The -e parameter will execute the command you specify as argument and will bind it to the connection.
This can enable us to execute a shell (e.g. cmd.exe) and bind it to a connecting machine, effectively giving the remote end access to our machine.

Due to the reason above, builds with the -e option can be flagged as malicious by some antiviruses,
so it is recommended to avoid using them.

### Command line arguments
        -d              detach from console, background mode
        -g gateway      source-routing hop point[s], up to 8
        -G num          source-routing pointer: 4, 8, 12, ...
        -h              this cruft
        -i secs         delay interval for lines sent, ports scanned
        -l              listen mode, for inbound connects
        -L              listen harder, re-listen on socket close
        -n              numeric-only IP addresses, no DNS
        -o file         hex dump of traffic
        -p port         local port number
        -r              randomize local and remote ports
        -s addr         local source address
        -c              send CRLF instead of just LF
        -u              UDP mode
        -v              verbose [use twice to be more verbose]
        -w secs         timeout for connects and final net reads
        -z              zero-I/O mode [used for scanning]
        -e prog         inbound program to exec [dangerous!!]

### Examples
1. listen to TCP port 1234 (re-listen on close) and be verbose
        
        nc -v -L -p 1234

2. Connect to 127.0.0.1 port 80 and be verbose

        nc -v 127.0.0.1 80

3. Test connection to 127.0.0.1 port 80 and print a message if we cannot connect 

        nc -z 127.0.0.1 80
        IF %ERRORLEVEL% NEQ 0 ECHO Could not connect to 127.0.0.1:80
    