# boxstarter-probrem-reproduction-for-win81

Reproduce the phenomenon that Boxstarter installation from the web does not
work correctly on Windows 8.1, using Vagrant.

## TL;DR

1. Run `vagrant up` to create a VM to access the URL:
   <https://boxstarter.org/package/boxstarter>
2. After a short wait, The setup will ask permission to run ClickOnce and
   UAC for Boxstarter installation, which you should follow there.
3. You can reproduce the problem in a terminal on guest Windows.

![Cannot process argument because the value of argument "type" is not valid. Change the value of the "type" argument and run the operation again. The specified module 'C:\ProgramData\chocolatey\extensions\boxstarter-choco\boxstarter-choco.psm1' as not loaded because no valid module file was found in any module directory.](https://raw.githubusercontent.com/kurone-kito/boxstarter-probrem-reproduction-for-win81/main/screenshot.png)

## Dependencies

- [Vagrant](https://www.vagrantup.com/)
  - some plugins
    - [Vagrant Reload Provisioner](https://github.com/aidanns/vagrant-reload)
    - [vagrant-vbguest](https://github.com/dotless-de/vagrant-vbguest)
- [VirtualBox](https://www.virtualbox.org/)

## Usage

Setup:

```sh
vagrant up
```

Teardown:

```sh
vagrant destroy -f
```

### Process

Execute the commands above, and the following processes will be performed
_entirely automatically except for some exceptional cases_.

1. Vagrant downloads the
   [jaswsinc/windows81](https://app.vagrantup.com/jaswsinc/boxes/windows81)
   image (4.21 GB). If a cache exists, it will be used.
2. Vagrant builds a virtual PC using the above image and Virtualbox.
3. Start the virtual PC and wait until Windows 8.1 has completed booting.
   - NOTE: It may wait an excessive amount of time here. It may look like a
     hang-up, but after a _few minutes of waiting_, it will progress
     because the service used to communicate between Vagrant and the guest
     Windows is configured by default to start only upon request.
4. Install the latest Virtualbox Guest Additions via the Vagrant Reload
   Provisioner plugin and reboot if necessary.
   - NOTE: After this reboot, you may have to wait a few minutes for
     reconnection, as in the previous section. It can remedy in the next
     step.
5. Vagrant will initiate a configuration to reproduce the problem that is
   the subject of this repository.
   1. Configure the Windows Remote Management (WinRM) service always to
      start so that it can connect in a short time on subsequent restarts.
   2. Deploy a batch script to a startup that accesses the
      <https://boxstarter.org/package/boxstarter> by the browser. It is a
      roundabout way of getting around that WinRM cannot interfere with
      the GUI and will run as a background process even if the browser is
      launched directly.
   3. Restart the virtual PC. At this point, your Vagrant duties are over,
      and control will return to the shell, but _you should continue to
      keep an eye on the behavior of the guest Windows_ running in
      Virtualbox.
   4. **`!`** The batch you add to Startup will ask the user for permission to run
      ClickOnce to launch Boxstarter from the URL, so
      **you hit the Run button**.
   5. **`!`** After the download, you will be asked to allow UAC, which
      **you should do**.
   6. Boxstarter installation begins and outputs the logs described below.

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
