# Unity preview DXR
This repository contains a preview DXR project.
This repository contains the Experimental DXR project.

You can clone the repository using the tool of your preference (Git, Github Desktop, Sourcetree, ...). 

  | IMPORTANT                                                    |
  | ------------------------------------------------------------ |
  | This project uses Git Large Files Support (LFS). Downloading a zip file using the green button on Github **will not work**. You must clone the project with a version of git that has LFS. You can download Git LFS here: <https://git-lfs.github.com/>. |

Project zip with all files (including LFS files) can be downloaded from the release section https://github.com/Unity-Technologies/Unity-Experimental-DXR/releases.

The Experimental DXR project is a Unity custom version with binaries based on the 2019.2a5 version of Unity, enhanced with DXR support and version 5.8.0 of HDRP enhanced with DXR support. It is a Windows 10 (64 bit) only version with DX12 API.

This project is a sandbox in which you can  play with real time ray tracing features in Unity. This is a prototype and the final implementation of DXR will be different from this version. This project can not be used to do any production work.

Requirements:
- NVIDIA RTX series card with the latest drivers [here](https://www.nvidia.com/Download/index.aspx?lang=com)
- Windows 10 RS5 (Build 1809) or later


Install step:
Download the project from Github in the release section, unzip.
Launch Unity.exe
Create a new project and select DXR High Definition RP (Preview) - Be sure you are to create project for Unity 2019.2.0a5.

See usage here: https://github.com/Unity-Technologies/Unity-Experimental-DXR/blob/master/documentation/The%20Experimental%20DXR%20project%20manual.pdf

Unity Forum Link: https://forum.unity.com/threads/unity-experimental-hdrp-dxr.656092/

Note: The binaries available on this github can be use with this branch from SRP github:
https://github.com/Unity-Technologies/ScriptableRenderPipeline/tree/experimental-dxr-release
This is the branch that is included inside the template in case users want to avoid to install the template project.

FAQ:
- I get " this application wont work on this computer" when running Unity.exe

You don't have all the files from the repository. This project uses Git Large Files Support (LFS). Downloading a zip file using the green button on Github **will not work**. You must clone the project with a version of git that has LFS. You can download Git LFS here: <https://git-lfs.github.com/>. 

- When installing the DXR project template I get this error:

<img src = "https://github.com/Unity-Technologies/Unity-Experimental-DXR/blob/master/documentation/Error0.png" >

This is due to Windows limitation that can't handle more than 260 character for filename. 
Please use a shorter folder and project name to allow the template to install correctly. Like "C:\DXR"

# Techniques using DXR:
* Ambient occlusion
* Rough Reflection (including lighting in reflection)
* Texture rectangle light with shadow
* Primary-ray rendering  multi-hit smooth transparent and opaque


All techniques but primary ray for realtime raytracing rely on having access to depth and normal buffer which is also used for denoising. In HDRP we have these buffers in both forward and deferred mode.
The technique of area light shadow that we use require a GBuffer, mean our forward material aren’t compatible with it (StackLit, Fabric…)


Current state:
* General:
   * Random number generation for coherent spatially and temporally effect (i.e compatible with TAA)
   * Most effects use a temporal accumulation on the non denoised previous frames (require history buffer for each effect) and then apply a simple denoiser (separable bilateral blur).
   * Simple firefly clamping
   * We handle correctly single and double sided object
* Material:
   * Alpha cutoff support for all effects. Currently we handle alpha cutoff like transparent object in DXR and use a threshold
   * Lit and Unlit shader are support
      * It doesn’t cover 100% of lit shader features however
   * Lit and HD Unlit master node are supported
   * We use an approximation with a single ray for the mipmapping of texture (There is no ddx, ddy with raytracing to get mipmap and ray differential is too costly - Need to forbid node in shader graph using ddx/ddy).
   * Transparent support IOR, absorption etc… with Primary-ray (no support for blending mode)
* Lighting
   * Ambient Occlusion: We replace SSAO pass by DXR AO pass
   * Material have instance mask flag to separate between category
      * AO and shadow: Transparent objects are ignored
   * Texture rectangular area lights with shadow. Use Eric Heitz’s Paper (Combining Analytic Direct Illumination and Stochastic Shadows). These are screen space shadow map. We currently have an array (limited at 4 currently) of screen space shadow for area light with an index to fetch it in the lightloop. This technique require access to full GBuffer, only one raytraced sample is required. This allows us to estimate the lighting with and without the visibility term. Two screen space textures produced are then denoised with same algorithm (we currently use a gaussian bilateral filter). 
      * Note: This technique is close to the reference but is not perfect, there is still artifact. However in term of performance it is fast. The other technique that consist of just producing a shadow map with visibility sample and denoise with NVidia technique give wrong result (still acceptable) but can be use in case we are in forward.
      * Only Lit shader is supported - Limitation of the technique
   * Reflection: We replace SSR pass by DXR reflection pass
      * Reflection is perform with secondary ray shoot from depth + normal buffer. Lighting is perform with the regular code and use HDRP light loop. Punctual shadow (directional, spot, point) rely on shadow map and use the shadow map atlas as well as the area light technique described above. Lightprobe, LPPV and Lightmap are supported. Rough reflection is supported with full screen and with a quarter resolution mode for performance with temporal smoothing (SEED temporal denoiser)
      * We use a spatial partitioning structure to store local light that we query for intersection position for reflection effect
      * Currently each objects setup in AS evaluates its lightprobe (In addition to lightprobe being evaluated in frustum for regular rasterization (need a cache system))
   * Support Light Layers

Limitation
* Caution: Node in Shader Graph with DDX/DDY instruction fail with DXR
   * Checkerboard
   * No support for Terrain which rely on DDX/DDY
* Multi GPU isn’t supported in Unity for now.
* Transparent don’t work with technique mention above that require depth and normal buffer. Currently Transparent need to be handled with rasterization unless we render them with Primary-ray.
* Transparent blend mode. With DXR transparent are hard to support. Transparent blending mode aren’t sent to the shader, so currently we can’t make distinction between additive and alpha blending. Currently we will only do alpha blending all the time.
* No support for vertex deformation (skinning, morph target, vertex animation)
* No support for visual effect graph

