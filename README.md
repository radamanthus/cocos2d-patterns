Cocos2D/Kobold2D Patterns
================

A repository of solutions to common Cocos2D/Kobold2D problems.

# Drawing

### Sprites

	int x = 100;
	int y = 100;
	CCSprite *aSprite = [CCSprite spriteWithFile:@"sprite.png"];
	aSprite.position = CGPointMake(x, y);
	[self addChild:aSprite];

### Text Labels

	aLabel = [CCLabelTTF labelWithString:@"Hello, World!!"
	                                           fontName:@"Marker Felt"
	                                           fontSize:24];
	aLabel = CGPointMake(400, 40);
	aLabel = ccGREEN;
	[self addChild:aLabel];

### Buttons

First, create a CCSprite (see Drawing Sprites above). Then create or modify the ccTouchesBegan method:

	- (void) ccTouchesBegan:(NSSet *)touches withEvent:(UIEvent *)event 
	{
		UITouch *touch = [touches anyObject];
		CGPoint location = [touch locationInView:[touch view]];
		location = [[CCDirector sharedDirector] convertToGL:location];
        if (CGRectContainsPoint([aSprite boundingBox], location)) {
            CCLOG(@"The object aSprite was tapped!");
        }
	}


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

TODO

# Misc

### Generate a Random number

This generates a random number between 1 and 100 (inclusive).

    (arc4random() % 100) + 1;



