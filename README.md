# Kubernetes Scheduling Visualizer

A premium, visual-first educational microsite that teaches Kubernetes scheduling through interactive simulations, animated visualizations, and a fully functional scheduler lab.

## Features

- **Interactive Scheduler Lab**: Simulate Kubernetes pod scheduling with real-time visualization
- **Visual Learning**: Animated diagrams explain scheduling decisions, constraints, and failures
- **25+ Concept Pages**: Comprehensive coverage of Kubernetes scheduling topics
- **Dark/Light Mode**: Fully themeable with persistent preference
- **Accurate Scheduler Model**: Implements filtering, scoring, and binding logic

## Getting Started

### Installation

```bash
npm install
```

### Development

```bash
npm run dev
```

The application will be available at `http://localhost:5173`

### Build

```bash
npm run build
```

### Preview Build

```bash
npm run preview
```

## Project Structure

```
src/
├── components/
│   ├── layout/          # Navbar, Sidebar, ThemeProvider
│   ├── ui/              # Reusable UI components (Button, Card, Badge)
│   └── visualizations/  # Cluster, Scheduler Flow visualizers
├── pages/               # Route pages (Home, Concepts, Lab)
├── stores/              # Zustand state management
├── types/               # TypeScript type definitions
├── lib/                 # Scheduler engine, utilities
└── data/                # Concept content data
```

## Scheduler Simulation

### What is Simulated

The Scheduler Lab implements a client-side simulation of Kubernetes scheduling with the following capabilities:

#### Scheduling Phases

1. **Filtering**: Nodes are filtered based on:
   - Resource availability (CPU, Memory requests)
   - Node selector requirements
   - Taints and tolerations
   - Node affinity rules

2. **Scoring**: Eligible nodes are scored based on:
   - Resource utilization (bin-packing algorithm)
   - Resource fragmentation
   - Pod count on nodes
   - Available resources

3. **Binding**: The pod is assigned to the highest-scoring node

#### Constraints Supported

- **Node Selector**: Simple label-based node selection
- **Node Affinity**: Required and preferred scheduling rules
- **Taints & Tolerations**: Control pod placement based on node taints
- **Priority Classes**: Affects scheduling order and preemption
- **Resource Requests/Limits**: CPU and memory allocation

#### Limitations of the Scheduler Model

The following Kubernetes scheduler features are **NOT** simulated:

1. **Horizontal Pod Autoscaler (HPA)**: Not simulated (though UI is available for cluster autoscaling concept)
2. **Custom Schedulers**: Only default scheduler behavior is implemented
3. **Volume Binding**: Storage-aware scheduling is not considered
4. **Pod Overhead**: Additional system resource overhead is not calculated
5. **Node Allocatable**: Uses full capacity instead of allocatable resources
6. **Extended Resources**: Only CPU and memory are supported
7. **Cordoned Nodes**: Node unschedulable status is not fully implemented
8. **Pod Disruption Budgets**: Not considered during scheduling decisions
9. **Topology Spread Constraints**: Not implemented
10. **Multiple Schedulers**: Only single scheduler simulation

### Scheduler Configuration

The scheduler engine supports these algorithms:
- **Bin Packing**: Consolidates pods onto fewer nodes (default)
- **Spread**: Distributes pods evenly across nodes
- **Random**: Selects nodes randomly (for learning purposes)

## Concepts Covered

### Kubernetes Fundamentals
- What is Kubernetes
- Control Plane Overview
- Cluster Architecture

### Pods & Nodes
- Node
- Pod
- Container vs Pod

### Scheduling Basics
- Scheduler Overview
- Scheduling Lifecycle
- Pending Pods
- Node Resources
- Requests vs Limits
- Bin Packing
- Node Selection

### Scheduling Constraints
- Labels & Selectors
- Node Affinity
- Pod Affinity
- Pod Anti-Affinity
- Taints & Tolerations

### Advanced Scheduling
- DaemonSets
- ReplicaSets
- Deployments
- Preemption
- Priority Classes
- Eviction

### Failures & Recovery
- Unschedulable Pods
- Why Pods Stay Pending
- Cluster Autoscaling
- Scheduling Failures & Debugging

## Tech Stack

- **React 18** - UI framework
- **TypeScript** - Type safety
- **Vite** - Build tool and dev server
- **TailwindCSS** - Styling
- **shadcn/ui** - UI component patterns
- **Framer Motion** - Animations
- **Zustand** - State management
- **react-router-dom** - Routing
- **react-syntax-highlighter** - Code highlighting
- **Lucide React** - Icons

## Browser Support

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)

## Accessibility

- Full keyboard navigation support
- ARIA labels on interactive elements
- Respects `prefers-reduced-motion` setting
- High contrast in both light and dark modes

## License

MIT License - Feel free to use this project for learning and educational purposes.
