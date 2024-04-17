# Skybox AI Generator by Genbox

Create stunning AI-generated skybox assets within Unity for use as HDRIs in game dev and immersive projects.


## Installation

Install from the Unity Asset Store
- Add this package to your assets from the Unity Asset Store.
- Go to `Window > Package Manager`
- Change the project scope to `My Assets`
- Find `GenboxAiSDK` and click `Install`.


### Pusher Package
The Genbox Ai SDK can be used standalone or optionally together with a Pusher websockets package. If installed, the Pusher package will use websockets to listen for any changes in the Asset Generation Process on Runtime and make updates accordingly, which should improve performance for your games on Runtime.

The Pusher library requires .NET Framework runtime:
- Set `Edit > Project Settings > Player > Api Compatibility Level` to `.NET Framework`.

Option 1: Install the Pusher package with git:
- Go to `Window > Package Manager`
- `+ > Add package from git URL...`
- Enter `https://github.com/pusher/pusher-websocket-unity.git#upm`

Option 2: Install the Pusher package with OpenUPM-CLI:
- `openupm add com.pusher.pusherwebsocketunity`

After installing the Pusher package on 2021.x.x versions you might get an error saying:

`Assembly 'Packages/com.pusher.pusherwebsocketunity/Packages/PusherClient.2.1.0/lib/net472/PusherClient.dll' will not be loaded due to errors: PusherClient references strong named Newtonsoft.Json Assembly references: 12.0.0.0 Found in project: 13.0.0.0.`

To resolve the issue go to `Edit > Project Settings > Player > Other Settings > Configuration > Assembly Version Validation` and disable `Version Validation`.

## Changelog
Refer to the changelog file [here](CHANGELOG.md).

## Unity Versions Support

2020.3 and newer.

## Getting Started

After importing the package, open `Packages > GenboxAiSDK > Scenes > SkyboxScene`.

**Note**: Demo scene uses Text Mesh Pro elements for runtime UI. If you haven't imported TMP Essentials
you will be prompted to do so after you load the scene. When you are done importing TMP Essentials,
reload the scene by either double clicking on it in the `Assets/Samples/GenboxAiSDK/Scenes`.

The scene contains two notable gameObjects:
- `Genbox Ai Generator` generates skybox textures and materials.
- `Genbox Ai Skybox Mesh` generates and configures a mesh which combines the skybox with a generated depth map.

## Generating Skyboxes at Runtime

To be able to generate assets on runtime you just need to follow these simple steps:

1. Play the scene. You will see the necessary elements to generate a new skybox. You can look around by clicking and dragging the mouse and zoom with the scroll wheel.
2. Enter a prompt, select a style, click generate.
3. Generated textures and materials are placed in the `Assets/Genbox Ai Materials` for use in your project.

## Generating Skyboxes in Edit Mode

You can generate a new skybox that will replace the existing one by following these steps.

1. Select the `Genbox Ai  Generator` gameObject.
2. Select the desired style.
3. Fill in the `Prompt` field.
4. Click the `Generate Skybox` Button.
5. Generated textures and materials are placed in the `Assets/Genbox Ai  Materials` for use in your project.
6. You should see your new skybox in the game view. You can also click `Move Scene Camera to Skybox` to see the skybox in the scene view.

## Using the Skybox in your Scene

For detailed information on how skyboxes work in Unity, see [using skyboxes](https://docs.unity3d.com/Manual/skyboxes-using.html).

### Built-In Render Pipeline and Universal Render Pipeline (URP)

1. Go to `Window > Rendering > Lighting`.
2. Go to the `Environment` tab.
3. Drag the generated `skybox material` into the the `Skybox Material` field.
4. If you want to use the skybox as background lighting in your scene, ensure `Environment Lighting Source` is set to `Skybox`, then click `Generate Lighting`.

### High-Definition Render Pipeline (HDRP)

1. Add a global volume to your scene: `GameObject > Volume > Global Volume`.
2. Drag the generated `HDRP volume profile` in to the `Profile` field.

## Mesh Creator

The `Genbox Ai  Generator` component generates a color texture and a depth texture, which are assigned to the skybox material.

The `Genbox Ai Skybox Mesh` component generates a Tetrahedron mesh to apply this material. You can configure the `Mesh Density` and `Depth Scale` fields. The mesh and material will be configured to apply the generated depth map to deform the mesh.

Try zooming in and out with the scroll wheel in play mode to see the effect of the depth scale!

If you want to use the generated mesh in your own scene, click `Save Prefab`, then drag the new prefab into your scene.