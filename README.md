# Simple Dialogues Pro Documentation

# Simple Dialogues Pro
Hello! Thanks for buying Simple Dialogues. This is a simple tool to create diverse dialogue trees that you can access via code to do whatever you want! This was made with programming in mind. An upgrade over the free version I made years ago in college, this asset has been rewritten from the ground up using the old one as a basis. It’s much cleaner in implementation, easier to edit in the future, and allows me to add more functionality.

## Namespace
I have moved the Simple Dialogues Pro scripts under its own namespace, to keep things clean. They are under the SevenTools.SimpleDialoguesPro namespace. To access them, you can add using SevenTools.SimpleDialoguesPro; to the top of your script.
## Dialogue Editor
After downloading Simple Dialogues Pro you can find the Dialogue Editor window by going to Window > Dialogue System.

Once you open it, it will probably tell you that you have nothing selected. First, we must give a GameObject the dialogues component! Choose a gameobject to act as your NPC, go to add a component, and search for DialoguePro or drag and drop it from the scripts folder (Located under Assets/SimpleDialoguesPro/. Note the gold diamond representing the correct script.

Now, when you have that GameObject selected and highlighted in the hierarchy, when you go to the Dialogue Editor it will show you a blank screen that allows you to add and remove trees!




### Trees
Trees are basically our workspace, inside of this area we can add all of our nodes. You can have as many trees as you want. To add a tree, you can either select the drop down from the top left (where all your trees are accessed), or press the center button.

Once you’ve done this you’ll see our new workspace available! To move around in this area you’ll want to hold down the middle mouse button and drag, this will allow you to scroll to all the bounds of the space.

Now we begin working. It should be mentioned that most of the functionality in Simple Dialogues is based on right click context menus.

Now you can add your first node by right clicking anywhere inside the grid space and hitting “Create First Node”

Once you’ve done that a window appears! From here you can do many things.

### Nodes
Nodes are our bread and butter, and contain our important information. Dialogue, triggers, etc. all go inside them. Nodes consist of a few elements. First the most obvious part, the big window in the middle, this section allows you to type your dialogue! There is also a -/+ button in the top left and right corners. These allow for quickly adding new window connections, or you can manually right click on the node, hit “Create Connection”, then right click elsewhere and select either “Create Dialogue Node” or “Create Decision Node”. Nodes also have triggers, but we’ll get to that in a bit.
All nodes also should have a start and end, these are automatically generated. An end may not show if you have a looping dialogue system. They mark where the nodes will reset to when using them in code, and when the current tree has ended.

Nodes have a few different types, they can either be a Dialogue window, a Decision window, or an Option. We’ll go over each type.
Dialogue Node
This is the most basic type of node, and it’s pretty self explanatory. This is a node for just normal dialogue text to go into. It can only ever have one connection to another node.

#### Decision Node
This node allows us to make decisions about where we want to go on the tree! If we want a window to have more than one branch, it has to be marked as a decision window. When you create a decision window, if it has no connections it will be yellow, indicating that it needs at least one, otherwise it will be green.

#### Option Node
This type of node you cannot create manually, they are results from a decision node. When you create a decision node, any nodes that are connected after that will be marked as option node. These are to represent responses to whatever that decision window is, for example:

Here you see option windows are shown in cyan.
#### Connections
Most of these nodes are created for you, but there are times you may want some windows to loop back together, or to revert to a previous node (such as a shop system). You can use the “Establish Connection” tool to do this. If you right click a node, hit “Create Connection” and then right click another window and hit “Establish Connection” those windows will now be connected! This doesn’t work with all windows, for example trying to make a connection between two nodes that already have a connection, or trying to connect a decision node to another decision node.


### Selecting Nodes
While nodes can be used easily from within the grid window, you can also edit them individually from within the inspector for very long passages or other features such as triggers. If you select a node, it will turn an orange color. If you look in the inspector, you will then see the inspector has changed to give you options. It offers a large text box you can type in. Notice typing in either box updates the other. Additionally below that it offers a space for triggers.
### Triggers
Triggers are a pretty simple, but powerful feature. On any given node you can add a trigger. It can be any number. Next to the “New Trigger” box, enter the name of trigger, then hit add. It will be added to a list below. You can delete a trigger by hitting the - symbol to the right of it. When you reach a point in a dialogue, you can check if it has any triggers and then create functionality based on that.

### Localization
New to Simple Dialogues Pro is the localization features. The first time you open the Simple Dialogues Pro grid view, it will generate a localization asset if one doesn’t exist (It comes with one by default that simply includes “English”. You can of course change this to whatever you want, though note unless you have a language with that name the examples will show no text)

This file should be located in the root folder of Simple Dialogues Pro and is called SD_Localization.

If you select this file, in the inspector you will have a list of strings. Each string should represent a language you wish to support. You should avoid duplicates, but there is currently no error checking on this. You can add whatever language you want to represent, real, fake, or otherwise. You must have at least one language. If none exist, it will automatically add a “Default” language.

Once you’ve added any languages you want, in the grid view where the nodes are, as long as you have at least one tree at the top left you will see a dropdown for the current language. If you change what language is selected, all the nodes will change to their text display of that language. For example when I create “Bobs Language” all text I previously had is now blank, as it was under the “English” language. I can see that text again by switching the dropdown back to the “English” option.

Anything you type under a language dropdown will be specific to that language, though Triggers are shared between languages.

This can of course be used to add proper new languages, or just alternative phrasings.
### Import/Export
New to Simple Dialogues Pro is the import and export feature. This will make it easy to more securely back up your dialogue, or copy dialogues.
Two options are provided, each with their own use cases, JSON and CSV. You can choose what type you would like to import or export to the left of the button on the left, through a dropdown.

#### JSON
The JSON option is going to be the easiest for copying and securing your files. It simply exports or imports a JSON file. Exporting from JSON also allows you to keep the positions of the nodes as they were originally placed, while CSV will not.
#### CSV
The CSV option is better for creating in another document such as Excel or google sheets, and then importing into Simple Dialogues Pro. There is very specific formatting to follow, but easy to follow.
The first line of the file is the name of the tree.
Every line following represents a single node, with each part separated by commas. Heres an example to break down.

0,"English:Hey|Spanish:Hola","1,2","Bob",”Smile”,”Cry”

The first value is the ID of the node. Every ID has to be unique. Importing a file with incorrect IDs will cause issues.

The second value is wrapped in quotations, and represents the core dialogue. For the language support, it has its own set of rules. First the language name, with a colon : separating it from the text. The text that follows represents that language. Then, if you have more languages, add a | symbol, and start with the next language. After you’ve entered all this dialogue, end the quotation wrapping.

The third value is what nodes this node connects to. This should also generally be wrapped in quotations. If this represents a decision node, you should list all the nodes it connects to, separated by commas as shown. For example this connects to nodes 1 and 2.

Finally, every value afterwards (which each should be wrapped in quotations) are triggers.
## Converting from the old Simple Dialogues
First it should be clear - before attempting any large conversions, I highly encourage you to always back up your project. Code is never perfect, and I wouldn’t want you to accidentally corrupt important files because of an unexpected issue.

I know there are some who may still be using the old free Simple Dialogues. For this purpose I’ve included a way to automatically convert a Dialogues component to the new DialoguePro component. Since this relies on accessing scripts that only exist if you have the original Simple Dialogues installed, it is included but commented out. If you find the file OldSystemConverter.cs (this is under Assets/SimpleDialoguesPro/Scripts/Editor), you can uncomment the file.

After uncommenting the file, and selecting a GameObject with a Dialogues component, there is a button that allows you to convert it. It will not delete the old Dialogues component, but will add a new DialoguePro component.
## Dialogue Coding
Once we have our tree setup, then we can access all of the data from code! Included within the package is an example, you can look through the basic example there to get a good idea of how a basic dialogue system could be setup with this. It allows you to see a few varieties of dialogue trees and how they can be used. Feel free to use these scripts themselves in your own projects.

### DialoguePro Component
The DialoguePro component is the actual component you put on your NPC and what is used to gain access to all the dialogue you need. Once you have a reference to this component, you can call the functions within it to get the data. We’ll go through some of those functions here.

Additionally the component has a couple debug options if you’re having trouble figuring out where things may be going wrong. These are bools on the DialoguePro component. printDebugs will post general debug information that shows what’s happening in the component. printDebugErrors will post anything that has gone wrong.

```markdown
Bool ResetToFirstTree()
This will set the current active tree to the first one in the list, instead of specifying a specific one. This can be useful if you only have one tree and don’t need to bother specifying its name. It will return whether this was successful. It may fail if there are no trees on the node.
Bool Reset()
This will reset the current node to the very first node in the tree. This may fail if the current tree is null. If so, you will want to use ResetToFirstTree() or SetTree(). It can also fail if the tree has no nodes.
Void SetLocalization(String)
This sets the current localization language to the one passed in via parameters. This is done on a component basis.
String GetCurrentLocalizationSetting()
Returns what current localization language the component is set to.
Bool SetTree()
This sets what tree we’re working in, and where the dialogue should be pulled from. Calling this function automatically resets the tree.
String GetCurrentTreeName()
Returns the name of the current tree.
Bool IsEndOfTree()
This simply returns whether the current node we’re looking at is an end node.
Bool HasTrigger()
Triggers whether this node has any triggers.
String[] GetTriggers()
Returns an array of all the triggers this node has.
String GetFirstTrigger()
Returns the first trigger in the list of triggers on the node. If this node has no triggers, return an empty string.
String GetLastTrigger()
Returns the last trigger in the list of triggers on the node. If this node has no triggers, return an empty string.
Bool Next(Optional String)
This moves our current node we’re looking at to the next node in the tree. It has an optional string that will allow selecting a choice if this is a decision node. It returns if it was successful. If this is the last node, it will return false. If it couldn’t find the given choice, it would return false. 
String[] GetChoices()
Returns an array of strings of all the choices this current node has stored.
String GetCurrentDialogue()
This returns the current dialogue of the node we’re looking at.
```


## Feedback
Thanks for looking into Simple Dialogues! I already have future plans to support and add to this asset. If you have any feature suggestions or bug reports to make, please email in detail to KoseckCory@gmail.com. If you would prefer, I also have a Discord server you can join for support at https://discord.gg/HkHjVVXqMn
