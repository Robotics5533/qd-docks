# Swap Memory

in certain senarios its possible that the rio can run out of memory running complex problems,
this *shouldn't* happen, but is a very real problem for python bots that tend to be memory heavy
on the Robo-Rio 1

as a prior warning, languages other than python don't (often) suffer from that problem so mabye
keep that in mind when picking languages

one solution for this is to use **swap memory** in order to increase the avialable memory space of the
Rio. The correct solution is definitly to re-optimize code, but if thats not an option adding swap
to the RIO provides a temporary work around

## UUID

the uuid of a storage device is a unique identifier that marks that device,
we need these to specify which device we want to swap. While there might be (is) a way
to auto select a usb, using the UUID ensures you have the right device on the rio

that means WE NEED to figure out the id

there are several different commands that you can use
to find the UUID depending on the system that you are on

on linux systems (tested on arch specifically)
```bash
sudo blkid
```

```powershell
wmic path win32_computersystemproduct get UUID
```

example command output looks something like 
/dev/sda3: UUID="7b2c7efe-9cd3-4812-8dd9-284377e72f63" BLOCK\_SIZE="4096" TYPE="ext4" PARTUUID="c4bd465d-0b9f-0349-aa3d-7b8e0864356d"
