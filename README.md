# ForgedInvariant ![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/ChefKissInc/ForgedInvariant/main.yml?branch=master&logo=github&style=for-the-badge) [![Release Badge](https://img.shields.io/github/release/ChefKissInc/ForgedInvariant?include_prereleases&style=for-the-badge&sort=semver&color=blue)](https://github.com/ChefKissInc/ForgedInvariant/releases) [![Downloads Badge](https://img.shields.io/github/downloads/ChefKissInc/ForgedInvariant/total.svg?style=for-the-badge)](https://github.com/ChefKissInc/ForgedInvariant/releases/latest) ![Optimized by AI](https://img.shields.io/badge/optimized_by-AI-blue?style=for-the-badge)

The plug & play kext for syncing the TSC on AMD & Intel.

The ForgedInvariant project is Copyright © 2024-2025 ChefKiss. The ForgedInvariant project is licensed under the `Thou Shalt Not Profit License version 1.5`. See `LICENSE`

Click [here](https://chefkiss.dev/applehax/forgedinvariant/) for more information.

## Boot arguments

| Argument       | Effect                                                              |
| -------------- | ------------------------------------------------------------------- |
| `-FIOff`       | Disable the kext.                                                   |
| `-FIDebug`     | Enable debug logging (Debug builds).                                |
| `-FIBeta`      | Allow loading on unsupported (newer) macOS versions.                |
| `-FIPeriodic`  | Force periodic TSC sync even if the CPU can lock/adjust the TSC.    |
