#Fast Stats

Fast Stats is designed for benchmarking GPU Accelerated Flash content with as little performance impact as possible. 

The core goal is to provide a Stats package which works with all major 2D rendering engines, so we no longer need to use different libs depending on the project.

![alt FastStats](https://github.com/esDotDev/FastStats/blob/master/screenshot/screen.png?raw=true)

Unlike other Stats packages, which rely on displayList, TextFields and Graphic's API, FastStats uses cached textures to render everything. This allows it to be easily optimized for GPU based rendering.

FastStats currently supports the following rendering engines:

* Native DisplayList
* Starling
* ND2D

##Sample Usage

In it's most basic form you simply pass a reference to your root displayObjectContainer. This can be your stage, or any generic sprite:

	new FastStats(regularSprite);

Starling is similar:

	new FastStatsStarling(starlingSprite)

ND2D as well:

	new FastStatsND2D(node2d);

By default, FastStats will update itself every 1000ms, but this is customizeable:

	new FastStats(stage, 500); //Update every 500ms instead

If you would like to hide the background, that is optional:

	new FastStats(stage, 1000, false);

If you would like to position the stats somewhere other than the top, use a Sprite as your root:

	new FastStats(myContainerSprite);
	myContainerSprite.x = 100;

FastStats also supports the ability to display the total SpriteCount for a scene, but you must update it manually from somewhere in your application. This way, we're not wasting CPU cycles trying to trace your sceneGraph:
	
	FastStats.numChildren = 120;

If you would like to hide FastStats, use .visible:
	
	var stats:FastStats = new FastStats(this);
	fastStats.visible = false;

You can also specify visibility as the 4th constructor arg:

	new FastStats(this, 1000, true, false);

Finally, FastStats exposes the current FPS through a static property, so you can use it get your FPS anywhere in your application.

	trace(FastStats.fps); 