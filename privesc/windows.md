# Security Updates

    wmic qfe get Caption,Description,HotFixID,InstalledOn

## Check if an update is installed

    wmic qfe get Caption,Description,HotFixID,InstalledOn | findstr /C:"KB123123"

# Query Registry

    reg query HKCU\SOFTWARE\Policies

## Softwares

    reg query HKEY_LOCAL_MACHINE\Software\Policies
    reg query HKEY_LOCAL_MACHINE\Software\Policies\Microsoft

# Search

    dir /s *password*
    findstr /si password *.xml *.ini *.txt