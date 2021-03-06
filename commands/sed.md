# Sed

## [Tip] Use Sed To Manipulate SVG Files

### Description

If you have a SVG file and you want to edit it using command line quickly. You can use **Sed** (or any other text manipulation tool). Try to open the SVG file using text editor and you would see a lot of specifiers and things which you can change using Sed and other tools.

### Solution

For example, if you want to change a text called "DUMMY TEXT" into "NEW TEXT" in a SVG file, you can run the following command:

    sed "s/DUMMY TEXT/NEW TEXT/g" old.svg > new.svg

A new.svg file would be created containing the new text instead of the old. You can do the system process for anything you need in the SVG file.

### Additional Info

Check the [description of SVG files](https://inkscape.org/en/develop/about-svg/) in order to understand what you can change to obtain the results you want.

This method is what FOSS Notes uses by the way to generate notes' thumbnails automatically using a Bash script. Nobody has the time to design all of this manually.


## [Note] Sed Causes Files To Become Empty

### Description

If you are using Sed like this:

    sed -e s/STRING1/STRING2/g oldfile > newfile

Then you may notice that the contents of **newfile** are empty. This is because the **>** operator makes the Shell understands that it should open that file for writing. Which instantly removes all the contents from the file.

### Solution

A simple workaround would be:

    sed -e s/STRING1/STRING2/g oldfile > newfile.tmp && mv newfile.tmp newfile


