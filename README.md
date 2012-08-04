Cocos2D/Kobold2D Patterns
================

A repository of solutions to common Cocos2D/Kobold2D problems.

# Drawing

### Sprites

### Text Labels

### Buttons

# Configuration

### Initializing properties from a config.lua file

Create a config.lua file with this section:

    MyConfig = 
    {
        NumberOfPigs = 50,
        NumberOfCows = 20,
        NumberOfChickens = 30,
    }

Then run this:

    [KKConfig injectPropertiesFromKeyPath:@"MyConfig" target:self];
    
The above KKConfig call will be like running the following code:

    self.numberOfPigs = 50;
    self.numberOfCows = 20;
    self.numberOfChickens = 30;

# Scenes

To switch from OriginLayer to TargetLayer:

1. Add this class method to TargetLayer.

		+(CCScene *) scene
		{
			CCScene *scene = [CCScene node];
			TargetLayer* layer = [TargetLayer node];
			[scene addChild: layer];
		
			// return the scene
			return scene;
		}
		
2. From OriginLayer:

		CCScene* trans = [CCTransitionFlipY transitionWithDuration:0.2 scene: [TargetLayer scene]];
  		[[CCDirector sharedDirector] replaceScene: trans ];
		
You can replace CCTransitionFlipY with any of the transitions defined in CCTransition.h
    

# Audio

# Misc

### Generate a Random number

This generates a random number between 1 and 100 (inclusive).

    (arc4random() % 100) + 1;



