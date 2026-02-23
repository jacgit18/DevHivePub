---
excalidraw-plugin: parsed
tags:
  - excalidraw
  - codeSnippet
  - twoPointer
author:
  - jacgit18
  - chatgpt
Status: Done
Comments: 
Purpose: 
Started: 2024-04-04
EditDate: 
Relates: 
dg-publish:
---
![[Leetcode 75]]
Doesn't display since code snippets

Ask yourself how many swap checks 
makes sense
## Explained
Alright, imagine you have a bunch of colorful balls, and you want to arrange them in a certain order. You have red balls (represented by 0), blue balls (represented by 1), and green balls (represented by 2).

Now, we want to organize these balls in such a way that all the red balls are on the left side, followed by the blue balls, and then the green balls on the right side.

So, we have three baskets: one for red balls (left), one for blue balls (middle), and one for green balls (right). Our goal is to sort these balls by moving them into the correct baskets.

Here's how we do it step by step:

1. **Create Pointers:** We have two special friends, one standing on the left side and the other on the right side. They are helping us organize the balls. Let's call them Lefty and Righty.

2. **Start Sorting:** Now, we go through each ball one by one (represented by the `i` variable).

3. **If it's a Red Ball (0):** If the ball is red, we quickly swap it with the ball that Lefty is pointing to. Lefty then takes a step to the right, and we also move our finger (i) to the next ball.

4. **If it's a Green Ball (2):** If the ball is green, we do a similar swap with the ball that Righty is pointing to. But, we don't move our finger (i) immediately because the ball we swapped might be red or blue. We leave it for the next round to check.

5. **If it's a Blue Ball (1):** If the ball is blue, we just move our finger to the next ball without any swapping. No need to involve Lefty or Righty for blue balls.

6. **Keep Going:** We repeat these steps until our finger (i) reaches the same spot as Righty. That means we've checked and organized all the balls.

By doing this, we cleverly use Lefty and Righty to put the red balls on the left, green balls on the right, and blue balls in the middle, just like magic! And that's how we sort these colorful balls using a cool trick in our code.

==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==



# Alt Section


```javascript
function sortColors(nums) {
    let left = 0; // Pointer for 0s
    let right = nums.length - 1; // Pointer for 2s
    let i = 0; // Current element pointer

    while (i <= right) {
        if (nums[i] === 0) {
            // If current element is 0, swap it with the element at the left pointer
            [nums[i], nums[left]] = [nums[left], nums[i]];
            left++; // Move left pointer to the right
            i++; // Move current pointer to the right
        } else if (nums[i] === 2) {
            // If current element is 2, swap it with the element at the right pointer
            [nums[i], nums[right]] = [nums[right], nums[i]];
            right--; // Move right pointer to the left
            // Note: We don't increment i here because the swapped element at index i might be 0 or 1 and needs to be evaluated
        } else {
            // If current element is 1, simply move to the next element
            i++;
        }
    }
}
``` 




# Attempt
```javascript
function sortArray(nums) {
    let left = 0;
    let right = nums.length - 1;
    let index = 0;

    while (left < right) {
        // Swap if left is greater than or equal to right
        if (nums[left] >= nums[right]) {
            [nums[left], nums[right]] = [nums[right], nums[left]];
            right--;

        } else if (nums[right] > nums[left]) { // This condition seems redundant due to the while loop's logic
            left++;
        }

        // Additional swaps based on the index value
        if (nums[index] > nums[left]) {
            [nums[index], nums[left]] = [nums[left], nums[index]];
        }

        if (nums[index] > nums[right]) {
            [nums[right], nums[index]] = [nums[index], nums[right]];
        }

        index++;
    }
}
```



# Text Elements
# Element Links
MC6H74Ek: [[Leetcode 75#Alt Section]]
gv3QK9PC: [[Leetcode 75#Attempt]]

%%
# Drawing
```json
{
	"type": "excalidraw",
	"version": 2,
	"source": "https://github.com/zsviczian/obsidian-excalidraw-plugin/releases/tag/2.1.1",
	"elements": [
		{
			"type": "embeddable",
			"version": 724,
			"versionNonce": 18018768,
			"isDeleted": false,
			"id": "MC6H74Ek",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1084.0556527146775,
			"y": -945.574472711508,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 1035.520918118416,
			"height": 814.0240268683414,
			"seed": 28650,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1712261449687,
			"link": "[[Leetcode 75#Alt Section]]",
			"locked": false,
			"customData": {
				"mdProps": {
					"useObsidianDefaults": false,
					"backgroundMatchCanvas": false,
					"backgroundMatchElement": true,
					"backgroundColor": "#fff",
					"backgroundOpacity": 60,
					"borderMatchElement": true,
					"borderColor": "#fff",
					"borderOpacity": 0,
					"filenameVisible": false
				}
			},
			"scale": [
				1,
				1
			]
		},
		{
			"type": "embeddable",
			"version": 383,
			"versionNonce": 948316625,
			"isDeleted": false,
			"id": "gv3QK9PC",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 31.327358200390336,
			"y": -957.1234895901504,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 1341.111111111111,
			"height": 828.8888888888888,
			"seed": 72042,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1712261370328,
			"link": "[[Leetcode 75#Attempt]]",
			"locked": false,
			"customData": {
				"mdProps": {
					"useObsidianDefaults": false,
					"backgroundMatchCanvas": false,
					"backgroundMatchElement": true,
					"backgroundColor": "#fff",
					"backgroundOpacity": 60,
					"borderMatchElement": true,
					"borderColor": "#fff",
					"borderOpacity": 0,
					"filenameVisible": false
				}
			},
			"scale": [
				1,
				1
			]
		}
	],
	"appState": {
		"theme": "dark",
		"viewBackgroundColor": "#ffffff",
		"currentItemStrokeColor": "#1e1e1e",
		"currentItemBackgroundColor": "transparent",
		"currentItemFillStyle": "solid",
		"currentItemStrokeWidth": 2,
		"currentItemStrokeStyle": "solid",
		"currentItemRoughness": 1,
		"currentItemOpacity": 100,
		"currentItemFontFamily": 1,
		"currentItemFontSize": 20,
		"currentItemTextAlign": "left",
		"currentItemStartArrowhead": null,
		"currentItemEndArrowhead": "arrow",
		"scrollX": 1107.1722280652243,
		"scrollY": 1452.9489315093422,
		"zoom": {
			"value": 0.55
		},
		"currentItemRoundness": "round",
		"gridSize": null,
		"gridColor": {
			"Bold": "#C9C9C9FF",
			"Regular": "#EDEDEDFF"
		},
		"currentStrokeOptions": null,
		"previousGridSize": null,
		"frameRendering": {
			"enabled": true,
			"clip": true,
			"name": true,
			"outline": true
		}
	},
	"files": {}
}
```
%%