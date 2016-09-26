# MMButtonMenu
Floating menu control for iOS 8+ (as used in Mile Mapper)

## Installation
### Manually
Either clone or download this Repo. Then simply drag the MMButtonMenu folder to your Xcode project.

## Usage
First, create as many menu buttons as you want using `MMButtonMenuItem`:

    MMButtonMenuItem *menuButtonItem1 = [[MMButtonMenuItem alloc] init];
    
**Note:** You do **not** need to create a main menu button - it is created automatically by `MMButtonMenu`.

You can add actions to these buttons just like regular UIButtons:

    [menuButtonItem1 addTarget:self
                        action:@selector(doStuff)
              forControlEvents:UIControlEventTouchUpInside];
              
Next, create the button menu object and add the main menu buttons:
    
    MMButtonMenu *buttonMenu = [[MMButtonMenu alloc] initWithFrame:self.view.frame menuItems:[NSArray arrayWithObjects:menuButtonItem1, menuButtonItem2, menuButtonItem3, menuButtonItem4, nil]];
    
Finally, add the button menu to the view:

    [self.view addSubview:buttonMenu];
    
### Delegate
MMButtonMenu provides several delegate methods which should be fairly self explanatory:

    - (void)buttonMenuDidFinishAnimating;
    - (void)buttonMenuWillExpand:(MMButtonMenu *)buttonMenu;
    - (void)buttonMenuDidExpand:(MMButtonMenu *)buttonMenu;
    - (void)buttonMenuWillCollapse:(MMButtonMenu *)buttonMenu;
    - (void)buttonMenuDidCollapse:(MMButtonMenu *)buttonMenu;
    - (void)buttonMenuWillExpandSubMenuFromMenuItem:(MMButtonMenuItem *)menuItem;
    - (void)buttonMenuDidExpandSubMenuFromMenuItem:(MMButtonMenuItem *)menuItem;
    - (void)buttonMenuWillCollapseSubMenuFromMenuItem:(MMButtonMenuItem *)menuItem;
    - (void)buttonMenuDidCollapseSubMenuFromMenuItem:(MMButtonMenuItem *)menuItem;

Obviously, don't forget to set your delegate:

    buttonMenu.delegate = self;

### Submenus
You can add a horizontal submenu to any of the main menu buttons. Create your "submenu" buttons in the same way as the main menu buttons above. Then, add them to the desired main menu button with `setSubMenuItems:`:
    
    [menuButtonItem1 setSubMenuItems:[NSArray arrayWithObjects:subMenuButtonItem1, subMenuButtonItem2, nil]];

### Customization
#### Colours
Change button colours with the `backgroundColor` property:

    menuButtonItem.backgroundColor = [UIColor colorWithRed:200 green:191 blue:231 alpha:1];

The main menu button is accessed with the `mainMenuItem` property of the button menu.

    buttonMenu.mainMenuItem.backgroundColor = [MMUIManager primaryColor];

#### Button Images
You can add button images like so:

    UIImage *actionImage = [[UIImage imageNamed:@"action"] imageWithRenderingMode:UIImageRenderingModeAlwaysTemplate];
    [menuItem1 setImage:actionImage forState:UIControlStateNormal];
    
    UIImage *menuImage = [[UIImage imageNamed:@"menu"] imageWithRenderingMode:UIImageRenderingModeAlwaysTemplate];
    [buttonMenu.mainMenuItem setImage:menuImage forState:UIControlStateNormal];
    
## License
MMButtonMenu is available under the MIT license. See the LICENSE file for more info.
