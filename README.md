# Tracking Spatio-Temporal Phenomena
## Combine Aggregate Computing with Spatio-Temporal Neural Network
### Code repository

| Data generation | Alchemist Simulation
|-|-|
| [Link](https://github.com/cric96/scala-boids) | [Link](https://github.com/cric96/alchemist-boids) |

### Brainstoarming
In this document, I will discuss the idea behind the work that I started here in Aarhus.
The general idea is summarised in this figure:
![idea-1](https://user-images.githubusercontent.com/23448811/192802282-2662a2b2-5821-4c14-b918-bdeda065c83c.png)

In this work, we consider *Cyber-Physical Swarms* as a system of reference: they are systems composed of thousands/hundreds of entities that expose **collective** and **resilient** behaviours while achieving collective goals.
Particularly, here we wanna explore a *distributed* *collective* tracking approach: the nodes should follow spatiotemporal phenomena over time (e.g., fire in a forest, school of fish, moving people), in a way in which the nodes can cover the phenomena of interest. 
Moreover, the nodes should cover the space since they can control the whole selected region somehow.
The tracking concerns both the movement (i.e., the nodes should physically follow the changing data) both the data acquisition (i.e., the nodes should have a clear vision of the tracked sensing).
The latter is relevant to understand the distribution and making action using that information (i.e., in case of fire, the system should understand the centre and the border of it).

In this paper we would follow the following approach:
- for tracking the spatiotemporal phenomena, we would leverage a Neural Network that forecasts the next value of the perceived data
- using aggregate computing, we would like to control the system, e.g., by producing a movement field that moves the system toward the forecast information 

This integration could be useful for future work too, particularly, understanding how to use NN in an Aggregate Computing scenario could help us to improve the current solution in which we combine RL and AC (e.g., for power reduction, ...).

### Neural Network
![idea-2](https://user-images.githubusercontent.com/23448811/192802346-6fdc57c9-0d4e-43fc-81d2-2a4441358168.png)


### Training Schema
![idea-3](https://user-images.githubusercontent.com/23448811/192802423-36cbb91e-5f6e-4623-8505-f6a7d99de766.png)

### Training Data
![idea-4](https://user-images.githubusercontent.com/23448811/192802500-ad29cd52-8934-4c11-ba38-a495935125ef.png)

### Aggregate Computing & Neural Networks
![idea-5](https://user-images.githubusercontent.com/23448811/192802570-48968263-1bbb-42e2-889b-62ecd5d1991a.png)

### Todos
- [x] simulation tracking the spatial data
- [x] create the dataset
- [x] predict the next time step
- [x] integrate PyTorch in Alchemist
- [ ] direction field using forecast (? problem with the gradient evaluation)
- [ ] check the influence of the neighborhood size (? try to export feature instead of only the weight for the neural network) 
- [ ] check the influence of memory (? partially tried) 
- [ ] use time window instead of single value
### Library used
- [ScalaPy](https://scalapy.dev/): to make possible the interaction between Scala and Python
[Pytorch](https://pytorch.org/): the main framework for training the neural network
- [Pytorch Geometric](https://pytorch-geometric.readthedocs.io/en/latest/): library used for managing the spatial data (graphs)
- [Pytorch Geometric Temporal](https://pytorch-geometric-temporal.readthedocs.io/en/latest/): library used for the temporal extension of PyTorch geometric (kind of unstable currently, and with an unclean API)
