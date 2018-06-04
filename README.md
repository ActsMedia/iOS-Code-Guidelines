# ActsMedia iOS Design Guidelines

Basic guidlines for how to design and organize an ActsMedia iOS app

# General

All new code is to be written in Swift and should adhere to the [Swift API guidelines](https://swift.org/documentation/api-design-guidelines/)

3rd party dependencies should ideally be included in a way where we also have access to the source code, preferably as git-submodules.

## UI Design

Storyboards using native controls with autolayout should be used for most UI work and manipulation. It is clearly the direction Apple has been moving, and when done well it greatly reduces the amount and complexity of code in ViewControllers. 

Breaking up of a screen into multiple ViewControllers using ContainerViews is encouraged. It allows easier re-use of components and breaks up code in a logical manor.

To avoid navigational complexity and performance issues, multiple storyboards should be used. This can be done easily using `Editor->Move To Storyboard`.

To simplify use of storyboards and avoid run-time failures, always use [SwiftyIB](https://github.com/PeeJWeeJ/SwiftyIB) and dealing with segues or creating ViewControllers from storyboards. 

# Organization

## Code

### Files should be organized by usage, then type of utility or section of the application when necessary.

This allows quick navigation when moving between projects and simplifies naming when classes are re-used in different parts of an application

To avoid long lists of files at the same level, try to limit files in a folder to no more than 10 (not including folders).

**Example:**
    
    ->ViewControllers
        MainViewController
        ->Details
            DetailsViewController
            DetailsHeaderViewController
            DetailsContentViewController
        
    ->Storyboards
        MainScreen
        SplashScreen
    ->Views
        ->TableViewCells
            MainListTableCell
            DetailListTableCell
        ->CollectionViewCells
            MainCollectionViewCell
            DetailCollectionViewCell
        AsyncImageView    
        RoundedImageView
    ->Model
        ->ViewModel
        ->Database
        ProductSharedPreferences
    ->Controller
        FileManager
    ->Resources
        info.plist
        Assets.xcassets

