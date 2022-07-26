# boxstarter-probrem-reproduction-for-win81

Reproduce the phenomenon that Boxstarter installation from the web does not
work correctly on Windows 8.1, using Vagrant.

## Outputs

Excerpts only where errors occur:

```log
Cannot process argument because the value of argument "type" is not valid. Chang
e the value of the "type" argument and run the operation again.
The specified module 'C:\ProgramData\chocolatey\extensions\boxstarter-choco\boxs
tarter-choco.psm1' was not loaded because no valid module file was found in any
module directory.
```

<!-- markdownlint-disable MD033 -->
<details><summary>Full logs</summary>

```log
Boxstarter: Installing package boxstarter
Boxstarter Version 3.0.0.0
(c) 2018 Chocolatey Software, Inc, 2012 - 2018 Matt Wrock. https://boxstarter.or
g

Boxstarter: Disabling Automatic Updates from Windows Update
++ Boxstarter starting Calling Chocolatey to install boxstarter. This may take s
everal minutes to complete...
Boxstarter: SNAP! Chocolatey seems to be missing! - installing NOW!
Creating ChocolateyInstall as an environment variable (targeting 'Machine')
  Setting ChocolateyInstall to 'C:\ProgramData\chocolatey'
WARNING: It's very likely you will need to close and reopen your shell
  before you can use choco.
Restricting write permissions to Administrators
We are setting up the Chocolatey package repository.
The packages themselves go to 'C:\ProgramData\chocolatey\lib'
  (i.e. C:\ProgramData\chocolatey\lib\yourPackageName).
A shim file for the command line goes to 'C:\ProgramData\chocolatey\bin'
  and points to an executable in 'C:\ProgramData\chocolatey\lib\yourPackageName
'.

Creating Chocolatey folders if they do not already exist.

WARNING: You can safely ignore errors related to missing log files when
  upgrading from a version of Chocolatey less than 0.9.9.
  'Batch file could not be found' is also safe to ignore.
  'The system cannot find the file specified' - also safe.
chocolatey.nupkg file not installed in lib.
 Attempting to locate it from bootstrapper.
PATH environment variable does not have C:\ProgramData\chocolatey\bin in it. Add
ing...
WARNING: Not setting tab completion: Profile file does not exist at
'C:\Users\IEUser\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1'.
Chocolatey (choco.exe) is now ready.
You can call choco from anywhere, command line or powershell by typing choco.
Run choco /? for a list of functions.
You may need to shut down and restart powershell and/or consoles
 first prior to using choco.
Chocolatey v1.1.0
Installing the following packages:
boxstarter
By installing, you accept licenses for the packages.
Progress: Downloading BoxStarter.Common 3.0.0... 100%
Progress: Downloading boxstarter 3.0.0... 100%
Progress: Downloading BoxStarter.WinConfig 3.0.0... 100%
Progress: Downloading boxstarter.bootstrapper 3.0.0... 100%
Progress: Downloading boxstarter.chocolatey 3.0.0... 100%
Progress: Downloading Boxstarter.HyperV 3.0.0... 100%

BoxStarter.Common v3.0.0 (forced) [Approved]
boxstarter.common package files install completed. Performing other installation
 steps.

Type
  Confirmation (`-y`) is set.
  Respond within 30 seconds or the default selection will be chosen.
Cannot process argument because the value of argument "type" is not valid. Chang
e the value of the "type" argument and run the operation again.
The specified module 'C:\ProgramData\chocolatey\extensions\boxstarter-choco\boxs
tarter-choco.psm1' was not loaded because no valid module file was found in any
module directory.
Restricting write permissions of 'C:\ProgramData\Boxstarter' to Administrators
The Boxstarter.Common Module has been copied to C:\ProgramData\Boxstarter and ad
ded to your Module path.
You will need to open a new console for the path to be visible.
Use 'Get-Module Boxstarter.* -ListAvailable' to list all Boxstarter Modules.
To list all available Boxstarter Commands, use:
PS:>Import-Module Boxstarter.Common
PS:>Get-Command -Module Boxstarter.*

To find more info visit https://Boxstarter.org or use:
PS:>Import-Module Boxstarter.Common
PS:>Get-Help Boxstarter
Only an exit code of non-zero will fail the package by default. Set
 `--failonstderr` if you want error messages to also fail a script. See
 `choco -h` for details.
Environment Vars (like PATH) have changed. Close/reopen your shell to
 see the changes (or in powershell/cmd.exe just type `refreshenv`).
 The install of boxstarter.common was successful.
  Software install location not explicitly set, it could be in package or
  default install location of installer.

BoxStarter.WinConfig v3.0.0 (forced) [Approved]
boxstarter.winconfig package files install completed. Performing other installat
ion steps.

Type
  Confirmation (`-y`) is set.
  Respond within 30 seconds or the default selection will be chosen.
Cannot process argument because the value of argument "type" is not valid. Chang
e the value of the "type" argument and run the operation again.
The specified module 'C:\ProgramData\chocolatey\extensions\boxstarter-choco\boxs
tarter-choco.psm1' was not loaded because no valid module file was found in any
module directory.
Restricting write permissions of 'C:\ProgramData\Boxstarter' to Administrators
The Boxstarter.WinConfig Module has been copied to C:\ProgramData\Boxstarter and
 added to your Module path.
You will need to open a new console for the path to be visible.
Use 'Get-Module Boxstarter.* -ListAvailable' to list all Boxstarter Modules.
To list all available Boxstarter Commands, use:
PS:>Import-Module Boxstarter.WinConfig
PS:>Get-Command -Module Boxstarter.*

To find more info visit https://Boxstarter.org or use:
PS:>Import-Module Boxstarter.WinConfig
PS:>Get-Help Boxstarter
Only an exit code of non-zero will fail the package by default. Set
 `--failonstderr` if you want error messages to also fail a script. See
 `choco -h` for details.
 The install of boxstarter.winconfig was successful.
  Software install location not explicitly set, it could be in package or
  default install location of installer.

boxstarter.bootstrapper v3.0.0 (forced) [Approved]
boxstarter.bootstrapper package files install completed. Performing other instal
lation steps.

Type
  Confirmation (`-y`) is set.
  Respond within 30 seconds or the default selection will be chosen.
Cannot process argument because the value of argument "type" is not valid. Chang
e the value of the "type" argument and run the operation again.
The specified module 'C:\ProgramData\chocolatey\extensions\boxstarter-choco\boxs
tarter-choco.psm1' was not loaded because no valid module file was found in any
module directory.
Restricting write permissions of 'C:\ProgramData\Boxstarter' to Administrators
The Boxstarter.Bootstrapper Module has been copied to C:\ProgramData\Boxstarter
and added to your Module path.
You will need to open a new console for the path to be visible.
Use 'Get-Module Boxstarter.* -ListAvailable' to list all Boxstarter Modules.
To list all available Boxstarter Commands, use:
PS:>Import-Module Boxstarter.Bootstrapper
PS:>Get-Command -Module Boxstarter.*

To find more info visit https://Boxstarter.org or use:
PS:>Import-Module Boxstarter.Bootstrapper
PS:>Get-Help Boxstarter
Only an exit code of non-zero will fail the package by default. Set
 `--failonstderr` if you want error messages to also fail a script. See
 `choco -h` for details.
 The install of boxstarter.bootstrapper was successful.
  Software install location not explicitly set, it could be in package or
  default install location of installer.

boxstarter.chocolatey v3.0.0 (forced) [Approved]
boxstarter.chocolatey package files install completed. Performing other installa
tion steps.

Type
  Confirmation (`-y`) is set.
  Respond within 30 seconds or the default selection will be chosen.
Cannot process argument because the value of argument "type" is not valid. Chang
e the value of the "type" argument and run the operation again.
The specified module 'C:\ProgramData\chocolatey\extensions\boxstarter-choco\boxs
tarter-choco.psm1' was not loaded because no valid module file was found in any
module directory.
Restricting write permissions of 'C:\ProgramData\Boxstarter' to Administrators
The Boxstarter.Chocolatey Module has been copied to C:\ProgramData\Boxstarter an
d added to your Module path.
You will need to open a new console for the path to be visible.
Use 'Get-Module Boxstarter.* -ListAvailable' to list all Boxstarter Modules.
To list all available Boxstarter Commands, use:
PS:>Import-Module Boxstarter.Chocolatey
PS:>Get-Command -Module Boxstarter.*

To find more info visit https://Boxstarter.org or use:
PS:>Import-Module Boxstarter.Chocolatey
PS:>Get-Help Boxstarter
Only an exit code of non-zero will fail the package by default. Set
 `--failonstderr` if you want error messages to also fail a script. See
 `choco -h` for details.
 The install of boxstarter.chocolatey was successful.
  Software install location not explicitly set, it could be in package or
  default install location of installer.

Boxstarter.HyperV v3.0.0 (forced) [Approved]
boxstarter.hyperv package files install completed. Performing other installation
 steps.

Type
  Confirmation (`-y`) is set.
  Respond within 30 seconds or the default selection will be chosen.
Cannot process argument because the value of argument "type" is not valid. Chang
e the value of the "type" argument and run the operation again.
The specified module 'C:\ProgramData\chocolatey\extensions\boxstarter-choco\boxs
tarter-choco.psm1' was not loaded because no valid module file was found in any
module directory.
Restricting write permissions of 'C:\ProgramData\Boxstarter' to Administrators
The Boxstarter.HyperV Module has been copied to C:\ProgramData\Boxstarter and ad
ded to your Module path.
You will need to open a new console for the path to be visible.
Use 'Get-Module Boxstarter.* -ListAvailable' to list all Boxstarter Modules.
To list all available Boxstarter Commands, use:
PS:>Import-Module Boxstarter.HyperV
PS:>Get-Command -Module Boxstarter.*

To find more info visit https://Boxstarter.org or use:
PS:>Import-Module Boxstarter.HyperV
PS:>Get-Help Boxstarter
Only an exit code of non-zero will fail the package by default. Set
 `--failonstderr` if you want error messages to also fail a script. See
 `choco -h` for details.
 The install of boxstarter.hyperv was successful.
  Software install location not explicitly set, it could be in package or
  default install location of installer.

boxstarter v3.0.0 (forced) [Approved]
boxstarter package files install completed. Performing other installation steps.


Type
  Confirmation (`-y`) is set.
  Respond within 30 seconds or the default selection will be chosen.
Cannot process argument because the value of argument "type" is not valid. Chang
e the value of the "type" argument and run the operation again.
The specified module 'C:\ProgramData\chocolatey\extensions\boxstarter-choco\boxs
tarter-choco.psm1' was not loaded because no valid module file was found in any
module directory.
To load all Boxstarter Modules immediately, just enter 'BoxstarterShell'.
Interested in Windows Azure VM integration? Run CINST Boxstarter.Azure to instal
l Boxstarter's Azure integration.
Only an exit code of non-zero will fail the package by default. Set
 `--failonstderr` if you want error messages to also fail a script. See
 `choco -h` for details.
 The install of boxstarter was successful.
  Software install location not explicitly set, it could be in package or
  default install location of installer.

Chocolatey installed 6/6 packages.
 See the log for details (C:\ProgramData\chocolatey\logs\chocolatey.log).

Installed:
 - boxstarter.chocolatey v3.0.0
 - boxstarter v3.0.0
 - boxstarter.winconfig v3.0.0
 - boxstarter.common v3.0.0
 - boxstarter.bootstrapper v3.0.0
 - boxstarter.hyperv v3.0.0
++ Boxstarter finished Calling Chocolatey to install boxstarter. This may take s
everal minutes to complete... 00:03:54.2886254
True
Boxstarter: Restore Automatic Updates from Windows Update
Type ENTER to exit:
```

</details>
<!-- markdownlint-enable MD033 -->
