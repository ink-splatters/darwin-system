## Darwin system

`nix-darwin` + `home-manager` based, declarative `macOS` configuration. Early development. Poduction use is discouraged. 

### Platforms

`Apple Silicon` is first-class citizen. Intel would be likely broken out of the box, and there are no immediate plans to fix it. PRs are welcome, however.

### Misc

#### A note about Provisioning Profiles

Those are to be replaced by using corresponding _nix-darwin_ / _home-manager_ features.

###### `WARNING`: profiles can be evil. Installing password restrictions payloads (especially system-wide) is strongly discouraged unless you know what you are doing. There is a danger of lockout which, in [catastrophical corner case](docs/PROFILES.md#the-corner-case), is permanent and implies irrecoverable data loss.







