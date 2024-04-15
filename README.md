![image](https://github.com/AlSch092/UltimateAntiCheat/assets/94417808/bf94bb32-ab93-489e-815b-f1c35cae0c9d)

# UltimateAntiCheat: An Educational Anti-Cheat built in C++ (x64)

Research project: make an anti-cheat system to detect and/or prevent things like memory editing, debugging, unsigned code/certs, injected modules, etc.

   This project is meant to serve as a basic anti-cheat program for educational purposes and is not intended to be commercial software or overly complex to crack. This example includes basic but fundamental protections, and in production scenario we would aim to have many more detection methods along with a sophisticated server-side design. We aim to cover all attack surfaces such that the attacker is not able to gain a foothold into our process without being detected. Any modification to a single aspect will lead to being detected: for example, if someone tries to debug our code from usermode, they will likely re-map and perform memory edits to try and disable debugger detection which leads to their memory edit or remapping being detected. UltimateAntiCheat runs in usermode and has no driver associated with it. It's recommended that you run VMProtect or a similar program on the compiled binary for added security through obscurity.

   If there is anything not working for you (throws exceptions, can't build, etc) please raise an issue and I will answer it ASAP. If you have code suggestions or techniques you'd like to see added, or want assistance with adding anti-cheat to your game, please send me an email. More techniques and better design will be added to the project time permitting. 

## Current Detections and protective features:
- Detects unsigned Modules 
- Debugger detection (hardware, PEB, exceptions, kernelmode)
- Integrity checks on program memory (.text section checks, WINAPI hook checks)
- Remapping sections & re-re-mapping checks (anti-tamper)
- TLS Callback (anti-DLL injection)
- Parent process check
- Blacklisted Processes checks & whitelisted loaded modules check
- Loaded module name random renaming (process manipulation)
- Exported function names random renaming (process manipulation, anti-injection)
- Data obfuscation via templated type class
- Blocks DLL & symbol enumeration within certain tools such as Cheat Engine
- Encrypted Shellcode payload execution (requires a server to send data to this project)
- Check for if Windows is in 'Test Signing mode'

## Requirements
- For remapping to work in this project, /O2 must be enabled for optimization. Choosing other options might cause the program to throw exceptions.

## Updates
- April 7, '24: Added TestSigning / Windows 'test mode' detection 
- April 3, '24: Added WINAPI hook checking, blacklisted process checking
- March 31, '24: Detection methods have been moved to Detections class, techniques/prevention methods have been moved into Preventions class. Thus we have a set of detections and a set of preventions. Added detection looping to make the program feel more like a commercial AC. Code structure is closer now to where I had aimed originally. There's still much that can be added, stay tuned.
- March 25, '24: Beginning to move tests into their proper places and making use of the API class. Future updates will improve code structure and add threaded & looping support to make the program feel more like a commercial AC product and less like a techniques testing suite
- March 24, '24: A full re-upload was done along with various bug fixes. The program should compile without issues in x64 (x86 not supported yet, apologies). I plan on continuing work on this project in the near future. As it's been some time since making this project, lots more can be added soon with new knowledge and techniques acquired in the time between then and now. Stay tuned for further updates!
