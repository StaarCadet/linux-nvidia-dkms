# NVIDIA GPU Driver Playbook

This Ansible playbook is designed to permanently eliminate GPU driver falloff/outdate issues and prevent the Gnome Desktop from stopping. It is compatible with RedHat distributions (RHEL 7 and 8). The required installation files are included with the role for upload to anisble controller/source repository.

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [Variables](#variables)
3. [Notes](#notes)

## Prerequisites
- Dest var updated if wanted, default is /tmp

## Variables
- `filepath`: The path to the folder containing the NVIDIA installer and DKMS package
- `rhel7zip`: The name of the NVIDIA installer and DKMS package for RHEL 7
- `rhel8zip`: The name of the NVIDIA installer and DKMS package for RHEL 8
- `dkms7`: The name of the DKMS package for RHEL 7
- `dkms8`: The name of the DKMS package for RHEL 8
- `filename`: The name of the NVIDIA installer script

## Notes
- This playbook checks for GPU model compatibility before installation.
- If the playbook fails, it will indicate which computer and GPU model is causing the failure.
- To update the playbook, change the package name in the playbook and recreate the NVIDIA installer zip file.
- If updating the NVIDIA Driver package for a different GPU, edit the `vars.yml` file to match the GPU list provided by NVIDIA.
- The `nouveau` driver must be disabled before installing the NVIDIA driver. This playbook checks for the `nouveau` driver and disables it automatically.
- The X server must be stopped during installation. This playbook stops the X server and restarts it after installation.
