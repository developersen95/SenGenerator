# SenGenerator

Generate Swift properties for Xcode assets. No more "hardcoded" Strings!

At the moment, this script only supports Image and  Color assets. I will be adding support for other useful code generations such as storyboard identifiers, xib files, and segues in later versions.

## Installation

Code generation uses your `.xcassest` files to generate code. To run code generation as part of the Xcode build process, you need to create a build step that runs before "Compile Sources" to invoke the script.

1. Download and copy **SenGenerator.rb** to your **.xcodeproj** directory as the first step.
2. On your application target's **Build Phases** settings tab, click the **+** icon and choose **New Run Script Phase.**
3. In the created Run Script, change its name to **SenGenerator.**
4. Drag this new run script just above **Compile Sources** in your list of **Build Phases** so that it executes before your code is compiled.
5. Add below commands to the Run Script.

```bash
./SenGenerator.rb ${PROJECT_FILE_PATH} ${TARGET_NAME}
```
#### Arguments
1. Path of the **.xcodeproj** file. in this case `${PROJECT_FILE_PATH}`.
2. Name of the **Target**. in this case `${TARGET_NAME}`.
3. This is **optional**. Specify the path of the autogenerated swift file. If you don't specify the path it will create a file name **GeneratedResources.swift** by default in your target. `ex: RES/MyGEN.swift`

### Build your target
Now you can try building your target in Xcode. This will generate the **GeneratedResources.swift** file.

### Add the generated file to your target
Drag(or add using Xcode) the generated **GeneratedResources.swift** file to your target.

Uncheck the "Copy Files If Needed" checkbox since it should already be within your project's folder system. Then, make sure you've checked all the Targets the file needs to be included in.

## Usage

```swift
import UIKit

let image = UIImage(named: R.image.image_1) // no more UIImage(named: "image 1")
let color = UIColor(named: R.color.color_1) // no more UIColor(named: "color 1")
```

## Contributing
Pull requests are welcome. For major changes, please open an issue to discuss what you would like to change.

## License
[MIT](https://github.com/developersen95/SenGenerator/blob/master/LICENSE)
