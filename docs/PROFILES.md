## Configuration Profiles

TODO: description

### Danger of irrecoverable data loss

Password restrictions payloads needs to be used carefully. If the current password doesn't comply, one would be locked out. It might be not immediate
consequence. In anyway, it feels pretty scary and the symtom is loosing root access, above all.

If the profile is user-installable, it can be quite easily deleted without need for root access. But this might be not the case if the profile is system wide.

Login/Logout behavior is inconsistent when the system is booted, but it was impossible to login whatsoever, after reboot. In my case, resetting password
to make it comply the restrictions didn't work either. That's a point one would need RecoveryOS for sure.

#### The corner case

TL;DR. Once upon a time there was some precious data. R.I.P.

If SIP is off, it's relatively easy to kill `opendirectory` from main OS. Which, well, leads to very dangerous situation.

if FileVault is off at this moment, it can't be turned on (no admin access). If rebooting at this moment, neither main OS, nor RecoveryOS would be usable which 
**effectively renders all the data irrecoverable**. 

It might be that reboot would not make it too much worse. The lockout is really bad and means - new volumes cannot be mounted, existing mounts might stop working,
internet connection might stay intact but kernel will impose running processes starvation, I'm not aware if that's either deliberately or because of deadlocks
which are imminent if some crucial security daemons stop responding in the middle of some transactional operation.


#### Effective Remedy

File-Vault. It adds additional authentication authority (actually two of them: first is linked to `opendirectory`-originated "Crypto" User and the second is
failsafe and linked to FileVault Recovery code. Generally it means that no matter how badly `opendirectory` is damaged, even if the user's plist has been deleted, 
one would be _still able to login into Recovery and save the data_.
And if the Crypto user (corresponding to `opendirectory` user) is gone which sounds a bit rediculous, but I experienced that wihtout being able
to reproduce again: there is still a chance to be saved by entering FileVault Recovery Code.

Furthermore, with some tricks (before Ventura which might have killed it or it doesn't work because of a bug), the system even
could be fully recovered to working state, by decrypting the FileVault-ed volume, rebuilding `opendirectory` manually, make it consistant with `Preboot`,
finally issuing `resetpassword` to re-activate the system which would properly sign/HMAC all the related stuff / restore all the broken bits
of trusted boot chain.

**Do Turn the FileVault on. Always. It's not only secures your data**








