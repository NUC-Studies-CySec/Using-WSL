# Using-WSL
Windows Subsystem for Linux -WSL

The:

- [How](#-Installation),
- [Why](#-Why) and
- [Why not](#-Why-Not).

# Installation
## Simple installation for new Windows 10 OS (Version 20H2, Build 19042.746 or higher)

| Step # |	Description	| Command	| Comment |
|--------|--------------|---------|---------|
| 1	| Install WSL	| wsl.exe --install |	Run command, then restart the system (is required by). |
| 2	| List all Linux distributions available from Microsft | wsl --list --online | Follow steps from step  # 4 in the table below.|

## Older (version 20H2 or lower) Windows 10 

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

1) **Have access to Linux tools:** Use Linux tools from within Windows without having to use a dedicated Virtual Machine installation
1) **Compartmentalize working environment:** Use different Linux environments for diffferent purposes. 1 each for testing, production etc.
1) **Clean host environment:** Minimize installed applications on the Windows host.

### Use case - Have access to Linux tools
Having WSL gives access to a plethora Linux tools. Cygwin users will understand this immediately. Granted, many tools and applications are also available in windows. On the otherhand, having applications and tools running from WSL makes the "host" windows enviornment "clean".

Tools such as nmap, sqlmap, Nikto, awk, sed etc are available from WSL. WSL also enables one to run and test servers, application and services, which is best explained with next argument.

### Use case - Compartmentalize working environment
Developers may need to maintain GitHub repositories from different accounts. Spin up different servers to develop and test a web application. This can easily be done with WSL. WSL provides portability in that it can be packed, transfered and installed on another machine.

There are other options availiable, like running docker from windows which provides the similar compartmentalization. Lets examine how WSL may be better in the next use case.

### Use case - Clean host environment
I would prefer to run Docker from within WSL. From maintainability and recovery point of view, I recommend minimizing the amount of software installed on a system. Specially avoid installing software for testing on a "production" environment. This may introduce bugs, incompatibilities and ultimately bog down the system. Installing too many untested application is also a risk from the security point of view. A WSL distribution can be easily deleted, upgraded or replaced without leaving a whole lot of temporary configuration files, DLLs, etc on the host system.

## A concrete example
Requirements for my working, studies and testing environment:

- Windows 10 Pro is a requirement for peripheral device compatibility and other specific applications (Windows 10 just works).
- Free and OpenSource Software for cross platform compatibility, stability, and its free.
- Minimal footprint
- Transportability

Technology stack:

- WLS to run:
  - LaTeX - For writing papers
  - PlantUML - For writing models, diagrams and flowcharts
  - Graphviz - For rendering models, diagrams and flowcharts
  - Inkscape
  - VScode
  - Python
  - Anaconda/Jupyter Notebook
  - SQLite
  - Pandas

Using LaTeX, a type setting tool, to create professional looking papers and slides with math formulas etc rendered to PDF. PlantUML, combined with Graphviz and inkscape, to code models and diagrams to be rendered to png or svg files. Python for programming, SQLite for databse etc. are the tech stack which enables me to do everything I need from VScode to submit course assigments and papers

The stack makes collaboration, tracking changes and sharing via GitHub a breeze. The working folders are kept small and manageble, easy to backup and transfer. One can comfortably work from an old computer, even a Raspberry-Pi 4. Provided the destination has a spare screen and a set of mouse and keyboards, the Pi can be easily tucked in a pocket. My 2007 hardware (Core i5 2series, on 4 GB of ram on 125GB HDD laptop) has proved itself to be all that is required to get working.

# Why Not
WSL is not a virtual machine. It must not be perceived as security precaution as secure as a Virtual Machine installation.
