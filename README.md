# chainGpu Physics Simulation Tool
NON-COMMERCIAL USE ONLY

Tested on ```TouchDesigner 2022.32660``` for Windows.

## Description
chainGpu is a toolkit that allows you to simulate chain-like physics on the GPU using TouchDesigner. It is especially suitable for structures found in nature such as flowers, plants, grass, tentacles, hair and trees. Or any other use case where your imagination might take you. 

The calculations are done on a compute shader, and use a unique method where each segment posesses a target orientation, allowing it to calculate a linear velocity to get closer to that orientation. This results in organic looking movements which are fully compatible with other aspects, such as gravity, wind, turbulence, colliders etc. Please note that this approach is very different from most other physics simulations, a more common approach is to apply springs and make use of Verlet-integration. At this point I have yet to research the advantages or disadvantages compared with this method. It does however come with limitations in its current form.


## Demos
In the included toe file you'll find four demos, including annotation.

```basic_setup``` Example of the tox itself with nothing added. As you can see, quite a lot is already possible out of the box.

![til](https://github.com/mickeyvanolst/TD-chainGpu-Physics-Sim-Tool/blob/main/Preview/basic_demo.gif?raw=true)

```flower_demo_recursive``` By using multiple simulation instances, you can create complex animations that build on top of each other. Here you can see the flowers are anchored to the positions of the stem from the previous instance. Note that TD Chain Physics Sim can only handle 1D textures as an input.

![til](https://github.com/mickeyvanolst/TD-chainGpu-Physics-Sim-Tool/blob/main/Preview/flower_demo.png?raw=true)

```teapot_demo``` You can use 1D textures to spawn chains onto existing geometry, both the point positions and the normals can be used. This demo also showcases how to use the positions from the simulation in order to deform a Tube SOP. chainGpu Physics has build-in geometry intended for debugging, but is intended to simply supply the position and orientation data needed to build your own graphics.

![til](https://github.com/mickeyvanolst/TD-chainGpu-Physics-Sim-Tool/blob/main/Preview/teapot_demo.png?raw=true)

```hello_demo``` Due to the way we are calculating the forces based on orientations, we can actually supply our own target orientations. This demo shows how you can take the positions and normals of an existing path SOP and use it to initialize a physics chain.

![til](https://github.com/mickeyvanolst/TD-chainGpu-Physics-Sim-Tool/blob/main/Preview/hello_demo.gif?raw=true)

## Known issues and limitations (see Issue Log for details)
- This tool is still in development, beware of dragons.
- chainGpu is not intended to be a fully featured physics engine, neither is it a fully accurate representation of the real world, it will work well for some things.
- Due to an issue with GPU Texture buffer allocation, uncooking/cooking the parent comp where you place chainGpu, it will get comprimised data in its buffers, no matter if you reset the simulation. If anyone knows whats up, let me know.

## Roadmap (see Issue Log for details)
- [ ] Recursion, paving the way for linked structures such as L-systems, bones, etc. Currently you can use multiple instances of chainGpu Physics to achieve a similar effect.
- [ ] Self-collision, make chains collide with other chains and their own segments (will likely require binning method to remain performant).
- [ ] More options for colissions, repellers and attractors
- [ ] Arbitrary anchor points
- [ ] Elasticity
- [x] Compatibility with particlesGpu from the TD Palette

## Credits
I'd like to thank Atagen, Tim Gerritsen, Markus Heckmann, Josef Pelz and David Braun. This project has been inspired by their work, and includes knowledge and methods they shared with the community.

chainGpu has been developed by Mickey van Olst (2023). 

Portfolio: [mickeyvanolst.com](https://mickeyvanolst.com)

Instagram: [@mickeyvanolst](https://instagram.com/mickeyvanolst)

Please inquire for any commercial applications. Non-commercial use only, author must be credited.

Shield: [![CC BY-NC-SA 4.0][cc-by-nc-sa-shield]][cc-by-nc-sa]

This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg
