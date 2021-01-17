# Using-WSL
Windows Subsystem for Linux -WSL

The:

- [How](#-Installation),
- [Why](#-Why) and
- [Why not](#-Why-Not).

# Installation
Simple installation for Windows 10 OS Build 20262 or higher

| Step # |	Description	| Command	| Comment |
|--------|--------------|---------|---------|
| 1	| Install WSL	| wsl.exe --install |	Run command then restart is required by system |
| 2	| List all Linux distributions available from Microsft | wsl --list --online | Follow steps from step  # 5 in the table below.|

| Step # |	Description	| Command	| Comment |
|--------|--------------|---------|---------|
| 1	| Enable Windows Subsystem for Linux |	dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart	| N/A |
| 2	| Enable Virtual Machine	| dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart	| N/A |
| 3	| Determine what kind of Linux kernel update is required	| systeminfo \| find "System Type"	| Take note of the command output. This is the type of update required to be downloaded in the next step. |
| 4	| Download and Install Linux kernel update	| [WSL2 Linux kernel update package for x64 machines (windows.net)](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)	| Download package and run installation. <br><br> Restart the system.|
| 5	| Set WSL default to version 2	| wsl --set-default-version 2	| This is recommended for best performance. There are no disadvantages to switching to version 2. <br><br> Follow link for more details regarding the differences between the 2 verions: [Comparing WSL 2 and WSL 1](https://docs.microsoft.com/en-us/windows/wsl/compare-versions) \| [Microsoft Docs](https://docs.microsoft.com/en-us/windows/wsl/compare-versions) |
| 6	| Download Linux distribution from Windows Store. Use the app or brows to the link	| URL: [Microsoft Store (aka.ms)](https://aka.ms/wslstore)	| N/A |
| 7	| Launching the WSL distribution required user and password to be defined. Follow the instruction in the link	| [Create and update user accounts for Linux distributions \| Microsoft Docs](https://docs.microsoft.com/en-us/windows/wsl/user-support)| N/A |
| 8	| Install Windows Terminal from the Windows store	| N/A |	This terminal provides a better terminal windows compared to the default in Windows 10.|


# Why
Enables a seemless way to switch and work between Linux and Windows environments.

Disclaimer:

- It is assumed that one is initially running Windows by preferance, requirement or necessity. Because there is an argument that one can reverse the premise, run Linux as host, and have Windows run as a virtual machine. If you are the latter type of user, I guess none of the arguments provided below will be applicable for you.

## Use case
The "why" is perhaps best explained with use case arguments. I personally use WSL to:

1) **Access to tools:** Use Linux tools from within Windows without having to use a dedicated Virtual Machine installation
1) **Compartmentalization:** Use different Linux environments for diffferent purposes. 1 each for testing, production etc.
1) **Small Footprint, Clean Environment:** Minimize installed applications on the Windows host.

### Example to use case - Access to tools
Having WSL gives access to a plethora Linux tools. Cygwin users will understand this immediately. Granted, many tools and applications are also available in windows. On the otherhand, having applications and tools running from WSL makes the "host" windows enviornment "clean".

Tools such as nmap, sqlmap, Nikto, awk, sed etc are available from WSL. WSL also enables one to run and test servers, application and services, which is best explained with next argument.

### Example to use case - Compartmentalization
Developers may need to spin up some servers to develop and test a web application. Perhaps one needs to test different versions of said web application. This can easily be done from WSL. WSL also portable in that it can be packed, transfers and installed on another machine.

There is the option to install and run docker from windows. However, I would provided a counter-argument for on the next use case.

### Example to use case - Small Footprint, Clean Environment
I would prefer to run Docker from WSL. From maintainability and recovery point of view, I recommend to minimize the amount of software ones installs on a system. Avoid installing software for testing, just to be uninstalled again. This may introduce bugs, incompatibilities and ultimately bog down the system. Installing too many untested application is also a risk from the security point of view. A WSL distribution can be easily deleted, upgraded or replaced without leaving a whole lot of temporary configuration files, DLLs, etc on the host system.

## A concrete example
Requirements my working, studies and testing environment:

- Windows 10 Pro is a requirement for peripheral device compatibility and other specific applications. Windows 10 just works.
- Free and OpenSource Software for compatibility, stability, security and its free.
- Cross-platform compatibility
- Minimal footprint
- Transportability

Technology stack:

- WLS to run:
  - LaTeX - For writing papers
  - PlantUML - For writing modeling, diagrams and flowcharts
  - Graphviz - For mindmaps, diagrams and flowcharts
  - Inkscape
  - VScode
  - Python
  - SQLite
  - Pandas

Using LaTeX, a type setting tool, to create professional looking papers and slides with math formulas etc to PDF. PlantUML, combined with Graphviz and inkscape, to code models and diagram to be rendered to png or svg files. Python for programming, SQLite for databse etc. are the tech stack which enables me to do everything I want from VScode.

The stack makes collaboration, tracking changes and sharing via GitHub a breeze. The working folders are kept small and manageble, easy to backup and transfer. One can comfortably work from a Raspberry-Pi 4 (4GB). Provided the destination has a spare screen and a set of mouse and keyboards, the "PC" can be easily tucked in a pocket. My 2007 hardware (Core i5 2series, on 4 GB of ram on 125GB HDD laptop) has proved itself to be all that is required to get working.

# Why Not
WSL is not a virtual machine. It must not be perceived as security precaution as secure as a Virtual Machine installation.
