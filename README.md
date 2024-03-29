> ***Disclaimer*** This project has been deprecated in favor of [Whoami](https://github.com/ardaku/whoami)

- Whoami is ultimately the better implementation of this functionality, and as a result I see no reason to continue maintaining this repo.
- This codebase will continue to exist as a public archive.

# A simple Rust crate for host discovery

> Make more decisions based on the characteristics of the environment your code runs in.

- Basic Usage

```rust
use host_discovery::{Environment, CrossPlatform, LinuxSystem};

fn main() {
    let env = Environment::new();
    
    let os = env.get_os();
    let distro = env.get_distro();
    let arch = env.get_arch();
    println!("OS: {}, Linux Distribution: {}, Arch: {}", os, distro, arch);
}
```

- API Methods
> ***trait*** `CrossPlatform`
  
  - ***fn*** `get_os`: Returns a variant of OperatingSystem
  - ***fn*** `get_arch`: Returns a variant of Architecture
  - ***fn*** `get_cpu_cores`: Returns a u32 representing the number of physical cores on the CPU
  - ***fn*** `get_gpu_model`: Returns an optional String `Option<String>` containing the GPU model
  - ***fn*** `get_public_ip`: Returns String containing the public ip address
> ***trait*** `LinuxSystem`

  - ***fn*** `cpuinfo_model`: Returns a String containing the name of the CPU model
  - ***fn*** `get_distro`: Returns a String containing the name of the running Linux distribution
  - ***fn*** `get_cpe_name`: Returns a String containing the common platform enum
  - ***fn*** `get_hostname`: Returns a String containing the hostname of the machine
  - ***fn*** `is_subsystem_env`: Returns a boolean based on whether the Linux environment is a Windows subsystem
> ***trait*** `WindowsSystem`

  - ***fn*** `get_edition`: Returns a String containing the Windows edition via the registry
  - ***fn*** `get_win_hostname`: Returns a String containing the hostname of the machine
  - ***fn*** `get_cpu_model`: Returns a String containing the CPU model via the Windows registry
    
### Add to your project
```sh 
    cargo add host_discovery
```

> Planned Features

- API redesign to improve ergonomics and DRYness 
- Extended device detection (CPU, etc.).
- FreeBSD, MacOS, and extended Windows support

> ***If you experience any bugs, please don't hesitate to create an issue; so they may be fixed in a timely fashion.***

