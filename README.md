# fzfy-batteries

**Batteries-included library of fzfy modules**

A collection of ready-to-use fzfy configurations for common tools and workflows. Each module is organized in its own directory and can be imported individually into your fzfy setup.

## Available Modules

### kubectl

Hierarchical fuzzy menu for Kubernetes operations.

**Features:**
- Browse by resource type (Pods, Deployments, Services, etc.)
- Dynamic listing of resources from your current cluster
- Resource-specific operations (describe, logs, exec, delete, etc.)
- Returns commands without executing (so you can review/edit first)

**Usage:**

```yaml
# In your ~/.config/fzfy/fzfy.yaml
modules:
  kubectl:
    from: "/path/to/fzfy-batteries/kubectl/fzfy.yaml"
    trusted: true  # Required for dynamic kubectl queries

entries:
  - name: "Kubernetes"
    sublist: modules.kubectl
```

**Supported Resources:**
- Pods (with logs, exec, port-forward)
- Deployments (with scale, rollout operations)
- Services (with port-forward)
- ConfigMaps
- Secrets
- Nodes (with cordon/uncordon/drain)
- Namespaces
- StatefulSets
- DaemonSets
- Jobs
- CronJobs
- Ingresses
- PersistentVolumes
- PersistentVolumeClaims

## Installation

```bash
# Clone this repository
git clone https://github.com/guill/fzfy-batteries.git ~/.config/fzfy/batteries

# Import modules in your fzfy config
# See individual module documentation above
```

## Requirements

- [fzfy](https://github.com/guill/fzfy)
- fzf
- Tool-specific CLIs (kubectl, docker, etc.) depending on which modules you use

## Contributing

New modules are welcome! Each module should:
1. Live in its own directory
2. Have a `fzfy.yaml` entry point
3. Be documented in this README
4. Follow the hierarchical navigation pattern when appropriate
5. NEVER have side effects in variable evaluation

## License

MIT License
