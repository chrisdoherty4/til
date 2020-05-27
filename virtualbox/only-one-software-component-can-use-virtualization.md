# Only one software component can use virtualization hardware

VT-x and AMD-V are hardware virtualization technologies which add virtual
machine specific instructions to the ISA.

A Virtual Machine Montior (VMM) managed virtual machines deciding what to do
when a VM executes a privileged instruction via the `vmexit` and `vmentry` 
processes.

Only 1 VMM can control the virtualization hardware. This means you cannot
enable Hyper-V and VirtualBox simaltaneously. 