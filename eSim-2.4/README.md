🛠️ Bug Fixes and Installation Improvements for eSim on Ubuntu 24.04

📋 Overview
This repository documents the initial debugging and modification efforts to get eSim running on Ubuntu 24.04, which is not officially supported due to outdated dependencies and deprecated packages.

Focus was given to fixing critical installation issues found in:
install-eSim.sh
nghdl/install-nghdl.sh

Only the first two bugs were successfully fixed and verified due to time/resource constraints.

🐞 Bugs/Issues Reported and Fixed
✅ 1. python3-distutils Not Found 
Issue: python3-distutils package is deprecated and not available in Ubuntu 24.04.

Impact: The installation script fails during the Python environment setup.

Fix:
Installed setuptools, which is the modern replacement for distutils.
Modified install-eSim.sh to use setuptools instead.

📈 Difficulty: Moderate

📌 Importance: Affects main environment setup

✅ 2. pip3 Packages Could Not Be Downloaded
Issue: pip3 dependencies (like watchdog, hdlparse, etc.) failed to install due to permission or compatibility issues.

Fix:
Created a Python virtual environment.
Activated the environment inside install-eSim.sh before running pip commands.

📈 Difficulty: Moderate

📌 Importance: Affects installation of Python-based dependencies

⛔ Unresolved Issues
The following bugs were identified but not fixed due to time limits and the need for more complex workarounds or upstream changes:

❌ 3. KiCad 6.0 PPA Not Supported
Reason Not Fixed: Switching to another KiCad version requires more extensive testing and possible changes to GUI-related scripts.

❌ 4. LLVM 9 Not Available
Reason Not Fixed: While it's possible to upgrade the LLVM version in the script, this change can break compatibility with GHDL 0.37, which is used downstream.

❌ 5. GHDL 0.37 Fails with LLVM 14
Reason Not Fixed: GHDL's configure script doesn't support LLVM 14.0.6. Although patching is possible, the script gets overwritten automatically during the install, making the fix non-persistent without deeper changes.

📝 Notes
