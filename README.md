# RenderMethodDocs

#### **Warning**

> We don't recommend you learning render method if you don't have a basic understanding of Minecraft texture pack coding and how to edit entity files.

## 🔮 What is render method?
Render method is another method first used by Chainsketch and I that hasn't been used by the community like it should be. This method allows you to remove lag in an enormous amount by removing the amount of render controllers needed. For example, if you are rendering three numbers, you can render them all at once instead of having three render controllers for each digit.

## Pros and Cons of Render Method

✅ Pros:
- It is relatively easy to setup and can be renewed over and over.
- It removes unnessecary lag from packs especially "clients" that use many render controller for their "mods"

❌ Cons:
- You can only render up to three elements at a time. However, this is still better than 1, making the performance 3x better.

## 🤔 How to setup Render Mod?
First you need to create a material. This is the most important step, as this creates the render method.

Make a file called entity.material and put it in a folder called materials. This folder is like entity, models, animations, and etc.

```json
{
    "materials": {
        "version": "1.0.0",
        "render_method:wither_boss_armor": {
            "+defines": [
                "USE_MULTITEXTURE"
            ],
            "+states": [
                "DisableAlphaWrite"
            ],
            "msaaSupport": "Both",
            "+samplerStates": [
                {
                    "samplerIndex": 0,
                    "textureWrap": "Clamp"
                },
                {
                    "samplerIndex": 1,
                    "textureWrap": "Clamp"
                },
                {
                    "samplerIndex": 2,
                    "textureWrap": "Clamp"
                }
            ]
        }
    }
}
```

Now that you have defined this material, you need to make it accessible to the player. So go to the top part of the player.entity.json file. And follow my instructions.

Where you see the list of materials, add the material you just created like so:
```json
{
	"format_version": "1.10.0",
	"minecraft:client_entity": {
		"description": {
			"identifier": "minecraft:player",
			"materials": {
				"default": "entity_alphatest",
				"cape": "entity_alphatest",
				"animated": "player_animated",
				"render_method": "render_method"
			},
```

Finally, when you create your render controllers you can now render three at a time by applying this. For this example, I'm going to have a variable, thats set to a 3-digit number and it will render with just one render controller.

```json
"controller.render.my_first_var": {
    "geometry": "Geometry.my_first_vars_geo",
    "materials": [
        {
            "*": "Material.render_method"
        }
    ],
    "textures": [
        "array.d3[variable.my_var]",
        "array.d2[variable.my_var/10]",
        "array.d1[variable.my_var/100]"
    ],
    "filter_lighting": true,
    "ignore_lighting": true,
    "light_color_multiplier": 1.25,
    "arrays": {
        "textures": {
            "array.d1": [
                "Texture.d3_num0",
                "Texture.d3_num1",
                "Texture.d3_num2",
                "Texture.d3_num3",
                "Texture.d3_num4",
                "Texture.d3_num5",
                "Texture.d3_num6",
                "Texture.d3_num7",
                "Texture.d3_num8",
                "Texture.d3_num9"
            ],
            "array.d2": [
                "Texture.d4_num0",
                "Texture.d4_num1",
                "Texture.d4_num2",
                "Texture.d4_num3",
                "Texture.d4_num4",
                "Texture.d4_num5",
                "Texture.d4_num6",
                "Texture.d4_num7",
                "Texture.d4_num8",
                "Texture.d4_num9"
            ],
            "array.d3": [
                "Texture.d5_num0",
                "Texture.d5_num1",
                "Texture.d5_num2",
                "Texture.d5_num3",
                "Texture.d5_num4",
                "Texture.d5_num5",
                "Texture.d5_num6",
                "Texture.d5_num7",
                "Texture.d5_num8",
                "Texture.d5_num9"
            ]
        }
    }
}
```

## What are all of those "Texture" things about?
You need to define all of your textures in the array so you can use them properly. I attached all of the textures for numbers, in six digits [here](https://github.com/BedrockPlus/RenderMethodDocs/tree/main/numbers). Here is them listed down below, however you will have to change the directory to match your pack!

```json
"d1_num0": "CHYVES/tui/numbers/1_0",
"d1_num1": "CHYVES/tui/numbers/1_1",
"d1_num2": "CHYVES/tui/numbers/1_2",
"d1_num3": "CHYVES/tui/numbers/1_3",
"d1_num4": "CHYVES/tui/numbers/1_4",
"d1_num5": "CHYVES/tui/numbers/1_5",
"d1_num6": "CHYVES/tui/numbers/1_6",
"d1_num7": "CHYVES/tui/numbers/1_7",
"d1_num8": "CHYVES/tui/numbers/1_8",
"d1_num9": "CHYVES/tui/numbers/1_9",
"d2_num0": "CHYVES/tui/numbers/2_0",
"d2_num1": "CHYVES/tui/numbers/2_1",
"d2_num2": "CHYVES/tui/numbers/2_2",
"d2_num3": "CHYVES/tui/numbers/2_3",
"d2_num4": "CHYVES/tui/numbers/2_4",
"d2_num5": "CHYVES/tui/numbers/2_5",
"d2_num6": "CHYVES/tui/numbers/2_6",
"d2_num7": "CHYVES/tui/numbers/2_7",
"d2_num8": "CHYVES/tui/numbers/2_8",
"d2_num9": "CHYVES/tui/numbers/2_9",
"d3_num0": "CHYVES/tui/numbers/3_0",
"d3_num1": "CHYVES/tui/numbers/3_1",
"d3_num2": "CHYVES/tui/numbers/3_2",
"d3_num3": "CHYVES/tui/numbers/3_3",
"d3_num4": "CHYVES/tui/numbers/3_4",
"d3_num5": "CHYVES/tui/numbers/3_5",
"d3_num6": "CHYVES/tui/numbers/3_6",
"d3_num7": "CHYVES/tui/numbers/3_7",
"d3_num8": "CHYVES/tui/numbers/3_8",
"d3_num9": "CHYVES/tui/numbers/3_9",
"d4_num0": "CHYVES/tui/numbers/4_0",
"d4_num1": "CHYVES/tui/numbers/4_1",
"d4_num2": "CHYVES/tui/numbers/4_2",
"d4_num3": "CHYVES/tui/numbers/4_3",
"d4_num4": "CHYVES/tui/numbers/4_4",
"d4_num5": "CHYVES/tui/numbers/4_5",
"d4_num6": "CHYVES/tui/numbers/4_6",
"d4_num7": "CHYVES/tui/numbers/4_7",
"d4_num8": "CHYVES/tui/numbers/4_8",
"d4_num9": "CHYVES/tui/numbers/4_9",
"d5_num0": "CHYVES/tui/numbers/5_0",
"d5_num1": "CHYVES/tui/numbers/5_1",
"d5_num2": "CHYVES/tui/numbers/5_2",
"d5_num3": "CHYVES/tui/numbers/5_3",
"d5_num4": "CHYVES/tui/numbers/5_4",
"d5_num5": "CHYVES/tui/numbers/5_5",
"d5_num6": "CHYVES/tui/numbers/5_6",
"d5_num7": "CHYVES/tui/numbers/5_7",
"d5_num8": "CHYVES/tui/numbers/5_8",
"d5_num9": "CHYVES/tui/numbers/5_9",
"d6_num0": "CHYVES/tui/numbers/6_0",
"d6_num1": "CHYVES/tui/numbers/6_1",
"d6_num2": "CHYVES/tui/numbers/6_2",
"d6_num3": "CHYVES/tui/numbers/6_3",
"d6_num4": "CHYVES/tui/numbers/6_4",
"d6_num5": "CHYVES/tui/numbers/6_5",
"d6_num6": "CHYVES/tui/numbers/6_6",
"d6_num7": "CHYVES/tui/numbers/6_7",
"d6_num8": "CHYVES/tui/numbers/6_8",
"d6_num9": "CHYVES/tui/numbers/6_9"
```

## What if I don't need all three?
You must have all three filled out but if you want to leave one empty, just create a transparent image and use that for whatever slot you want empty. For example:

```json
"textures": [
    "Texture.blank",
    "array.d2[variable.my_var/10]",
    "array.d1[variable.my_var/100]"
],
```

## 📜 Special Credits
Documentation made by [chyves](https://github.com/notchyves)
