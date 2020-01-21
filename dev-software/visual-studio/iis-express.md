# IIS Express

## Failed to register URL, Access is denied \(0x80070005\)

**Starting the application on a specific port fails with "failed to register URL".**

**Fix 1**: Run this command in an admin prompt:

`netsh http add iplisten ipaddress=::`

Fix 2: Make sure no site in the config's is sharing ports. The config files can be found in both `%userprofile%/Documents/IIS Express` and `$(SolutionDir)/.vs` \(a hidden folder\).

