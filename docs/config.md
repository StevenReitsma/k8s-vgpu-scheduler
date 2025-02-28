# Config

you can customize your vGPU support by setting the following parameters using `-set`, for example

```
helm install vgpu-charts/vgpu vgpu --set devicePlugin.deviceMemoryScaling=5 ...
```

* `devicePlugin.deviceMemoryScaling:` 
  Float type, by default: 1. The ratio for NVIDIA device memory scaling, can be greater than 1 (enable virtual device memory, experimental feature). For NVIDIA GPU with *M* memory, if we set `devicePlugin.deviceMemoryScaling` argument to *S*, vGPUs splitted by this GPU will totally get `S * M` memory in Kubernetes with our device plugin.
* `devicePlugin.deviceSplitCount:` 
  Integer type, by default: equals 10. Maximum tasks assigned to a simple GPU device.
* `devicePlugin.migstrategy:`
  String type, "none" for ignoring MIG features or "mixed" for allocating MIG device by seperate resources. Default "none"
* `scheduler.defaultMem:` 
  Integer type, by default: 5000. The default device memory of the current task, in MB
* `scheduler.defaultCores:` 
  Integer type, by default: equals 0. Percentage of GPU cores reserved for the current task. If assigned to 0, it may fit in any GPU with enough device memory. If assigned to 100, it will use an entire GPU card exclusively.
* `resourceName:`
  String type, vgpu number resource name, default: "nvidia.com/gpu"
* `resourceMem:`
  String type, vgpu memory size resource name, default: "nvidia.com/gpumem"
* `resourceMemPercentage:`
  String type, vgpu memory fraction resource name, default: "nvidia.com/gpumem-percentage" 
* `resourceCores:`
  String type, vgpu cores resource name, default: "nvidia.com/cores"
* `resourcePriority:`
  String type, vgpu task priority name, default: "nvidia.com/priority"
