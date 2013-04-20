Gameboy Shader v0.2.2
=======
This shader for RetroArch is intended to simulate the LCD screen of the original dot matrix Gameboy (DMG). It is still a work in progress, so there may be issues including limited compatibility among different GPU profiles. 


//Requirements//////////////////////////////////////////////////////////////////////////////////////////////////////////

As of this commit, the requisites to run this shader are as follows:

-video driver set to "OpenGL" under RetroArch's video settings
-integer scaling disabled under RetroArch's video settings

If you follow the above two restrictions and the shader still doesn't work, it's like a GPU incompatibility issue. These should be worked out in future commits.


//Configuration options/////////////////////////////////////////////////////////////////////////////////////////////////

There are configuration options throughout the .cg files in the /shader_files/ directory that can be changed using any text editor to affect various visual effects. They can all be found under the "Config" header at the top of the files. Here's a list of configuration options and their default values:

////////////////
//gb_pass_0.cg//
////////////////

#define baseline_alpha 0.02 //the alpha value of dots in their "off" state, does not affect the border region of the screen

////////////////
//gb_pass_1.cg//
////////////////
#define blending_mode 1 //0 - only the space between dots is blending, 1 - all texels are blended
#define adjacent_texel_alpha_blending 0.1255  //the amount of alpha swapped between neighboring texels

////////////////
//gb_pass_4.cg//
////////////////
#define contrast 0.75 //analogous to the contrast slider on the original Gameboy, higher values darken the image - [0, 1]
#define shadow_opacity 0.75 //how strongly shadows affect the background, higher values darken the shadows - [0, 1]
#define shadow_offset_x 1.0 //how far the shadow should be shifted to the right in pixels - [-infinity, infinity]
#define shadow_offset_y 1.0 //how far the shadow should be shifted to down in pixels - [-infinity, infinity]


//Changing the palette and background images////////////////////////////////////////////////////////////////////////////

You will find the files for the palette and background in the /resources/ directory. These files can be edited or replaced using any image editor as long as you keep the format the same and filetype intact.

Color palette:
=======================
|          |          |
| BG Color | FG Color |
|  64x64   |  64x64   |
|          |          |
=======================
palette.png, 128x64

Background image:
==========
|        |
|        |
|        |
==========
background.png, 2048x2048

