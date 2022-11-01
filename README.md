## Darwin system

`nix-darwin` + `home-manager` based, declarative `macOS` configuration. Early development. Poduction use is discouraged.

If not stated otherwise, **Apple Silicon** platform should be always considered.

### Misc

#### A note about Provisioning Profiles

Those are to be replaced by using corresponding _nix-darwin_ / _home-manager_ features.

###### `WARNING`: profiles can be evil. Installing password restrictions payloads (especially system-wide) is strongly discouraged unless you know what you are doing. There is a danger of lockout which, in [catastrophical corner case](docs/PROFILES.md#the-corner-case), is permanent and implies irrecoverable data loss.







