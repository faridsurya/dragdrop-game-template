# Drag & Drop HTML5 Game Template

Drag & Drop HTML5 game template will help you to make drag & drop games very easily. You only need to prepare the pictures and sound assets then modify the JSON file provided without having to do the coding. This template has a categorization system that allows you to group games based on themes that you specify.

## Dependencies
html5 drag & drop game template requires several libraries including:
1. Pixi.js for main library of application
2. Dust.js for 
3. Carm.js 
4. Tink.js for the drag and drop activity
5. Howl.js for the sound management

## Installation
This template does not require special installation. Run the application on a web server, such as Apache.

## How to Custom or Add Game Assets?
There are two types of JSON files namely content.json and [category] .json. The content.json file will produce the main menu of the game which contains thumbnails of the categories you specify. In the package file given to you there are already two categories, namely transportation and robot. In the transportation category there are three images while the robot category contains one image. The contents of content.json file are:
``` 
[
    {
        "title":"Transportation",
        "id":"transportasi",
        "thumbnail":"./dragdrop/transportasi/car1/car1.png"
    },
    {
        "title":"Robots",
        "id":"robot",
        "thumbnail":"./dragdrop/robot/robot1/thumbnail.png"
    }
]
``` 

The id value is the id of the category. If you create a new category then you must add a new object to the content.json file and then create a folder in the dragrop folder with the same name as the id.

The file [category].json is located in the dragdrop/[category] folder. The example of content are:
```
{
    "screen":"poltrait",
    "music":"./robot/sound/backsound_after_school.mp3",
    "opening": 
    {
        "title":"./robot/game/opening_title.png",
        "titleSmall":"./robot/game/opening_title_small.png",
        "startButton":"./robot/game/btn_mulai.png",
        "background":"./robot/game/opening_bg.png"
    },
    "gamePlay":{
        "backgroundImage":"./robot/robot1/gameplay_bg.png",
        "dropSound":"./robot/sound/bounce_1.mp3",
        "assets":[]
}
}
```
The json code above is an example for the robot category. The explanation for each attribute is:

- `screen`: 
“poltrait” or “landscape”

- `music`:
The url of backsound music asset

- `opening`	
  `title`:
The url of title PNG image
`titleSmall`:
The url of top bar title image
`startButton`:
The url of button image for start the game
`backgroud`:
The url of background image in opening scene

- `gamePlay`
`backgroundImage`:
The url image of background game play scene
`dropSound`:
The url of sound that used in drop activity
`assets`:
The images contain of category


The structure of assets attribute in gamePlay contains:
```
{
    "name":"robot1",
    "scale":0.720844752,
    "played":false,
    "thumbnail":"./robot/robot1/thumbnail.png",
    "sound":
    {
       "drop":"./robot/robot1/sound/cartoon_boing.ogg",
       "win":"./robot/robot1/sound/sirine.mp3"                 
    },
    "parts":[]
}
```
- `name`:	The name of image in category
-  `scale`:	The scale of image when you make it. Read the further documentation for more information (calculate the scale value).
- `played':	Always false
- `thumbnail;:	Url of thumbnail image. It will display on the main menu of category.
- `sound`
`drop`:
Sound asset that will used when user drop the pieces
`win`:
Sound asset that will used when game was finished
- `parts`:	The data of slices of image


The structure of parts attribute are:
```
{
    "name":"robot-1-0",
    "url":"./robot/robot1/part_0.png",
    "isBody":true,
    "dropped":true,
    "target":{"x":0,"y":0}
}
```
- `name`:	Name of slice
- `url`:	Url of slice PNG image
- `isBody`:	True if that is main body of image. 
- `dropped`:	Always false
- `target`:	x and y coordinate of image slice. Give value of 0 if isBody is true. For other slice, read documentation below.

## Calculate the target value
The target value will determine where the piece should be dropped. The target value is relative to the main body. Calculation of the values of x and y for the target value are:

![calculate_target](https://user-images.githubusercontent.com/5952503/84209932-9f961c80-aae1-11ea-9330-82d080516cbf.png)

P1 is the center of mainBody (Car Body). P2 is the center of wheel image. X is width of rectangle and y is height of rectangle in pixel. Target value for x is the width and height for y value. If P2 is at right side of P1 then x is positive and vice versa. If P2 is at above of P1 then y value is negative and vice versa. For example, if the width is 300px and height is 150px then the target value is: {x:300, y:150}.

## Calculate the Scale Value
Scale value is the ratio of real size of piece and the development size.

![Screenshot from 2020-06-10 06-14-55](https://user-images.githubusercontent.com/5952503/84209982-c05e7200-aae1-11ea-893b-1299324c7cda.png)


The picture above shows that the scale value is a comparison between the value of the width in the image size and the width value in the development (794/620).


