# DrawableCopier
Python script for copying drawable resources into your Android project from an external `/res` directory. It will copy each `/res/drawable-*` resource to the destination directory's `/res/drawable-*` folder.

Perfect for use with [Roman Nurik's Android Asset Studio](http://romannurik.github.io/AndroidAssetStudio/icons-generic.html) or [Google's Material Design Icons](https://github.com/google/material-design-icons/releases)!


## Usage

Open up your favorite terminal. The script will provide you with confirmation messages of what will be copied before actually copying the files, giving you the option to cancel. Rest easy!

#### Basic

`>>> python drawable_copier.py <source_res_directory> <destination_res_directory>`

Example: If my Android Project is located at `/Users/jmhend/MyAndroidStudioProject` and the directory containing the resources I want to copy is at `/Users/jmhend/Desktop/material-design-icons-1.0.1/action`, the command will be:

`>>> python drawable_copier.py /Users/jmhend/MyAndroidStudioProject/app/src/main/res /Users/jmhend/Desktop/material-design-icons-1.0.1/action`



All resource files in the `<source_res_directory>` will be copied. Read on to see how to limit which files are copied.

The resource directories you supply as arguments must be the directories containing the `drawable-*` subdirectories. Also for now, each directory must be represented by a *full* directory path, i.e for example on Mac: `/Users/jmhend/MyAndroidStudioProject/app/src/main/res`, not `../.../main/res`


`<destination_res_directory>` is required.
`<source_res_directory>` will default to your current working directory if not supplied.

#### Extra

You can supply optional arguments to limit which files are copied with the `-f` flag:

`>>> python drawable_copier.py <source_res_directory> <destination_res_directory> -f ic_menu.png ic_action_new.png ...`

This will only copy `ic_menu.png` and `ic_action_new.png` from the source directories. This is especially useful when copying files from the Material Design Icons set.

The script also supports some basic file matching, using the `--filematch` optional argument:

`>>> python drawable_copier.py <source_res_directory> <destination_res_directory> -f ic_action --filematch`

This will copy all resources in the source directories containing the substring "ic_action". I.e, if there is `ic_action_new.png` and `ic_action_remove.png`, both will be copied. Again, you'll see a confirmation list of resources that will be copied before any copy action is made.
