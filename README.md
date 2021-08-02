# Graviton2 Linux kernel

## This is a Linux Kernel built specifically for the AWS Graviton2 processor, suitable for the environment -
- Ubuntu 20.04.2.0 LTS (Focal Fossa) Ubuntu 21.04 (Hirsute)
- EC2 instances including T4g, M6g and C6g (currently not tested for T4g)
- Kernel version is 5.11.22 
- Modified based on Ubuntu Hirsute , Ubuntu patches for AWS and AL2's configuration config-4.14.238-182.422.amzn2.aarch64


## Design principles - core of a high performance, safe production environment

## The modifications include but are not limited to these 
- Disabled useless device drivers such as Bluetooth, wireless, network card, printer, etc
- Commented the irrelevant Debug Settings
- Performance enhancements (as I understand it)
- Updated drivers for AWS ENA, EFA 
- Improved for aarch64, reference https://developer.arm.com/tools-and-software/open-source-software/linux-kernel
- Added BBRv2 support and made it the default setting for CONFIG_DEFAULT_TCP_CONG
- Added CONFIG_HW_RANDOM_GRAVITON patch
- Apply Clear Linux's atch allows the memory tuning for TCP
- enable O3 to compile
...

## The performance comparison （Based UnixBench ）
System Benchmarks Index Score on m6g.2xlarge instance

Amazon Linux 2's score is          6533.5

Ubuntu Ubuntu 20.04.2.0's score is 6456.2

The new kernel's score is          6841.8  (August 2, 2019)

