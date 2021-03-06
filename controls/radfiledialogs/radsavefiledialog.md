---
title: RadSaveFileDialog
page_title: RadSaveFileDialog
description: RadSaveFileDialog
slug: radfiledialogs-radsavefiledialog
tags: save,file,dialog
published: True
position: 5
---

# RadSaveFileDialog

__RadSaveFileDialog__ is a modal dialog box that allows you to specify a filename to save.

#### __Figure 1: RadSaveFileDialog__ 
![](images/radsavefiledialog-01.png)

## Showing the dialog

To show the dialog call its __ShowDialog__ method. If a valid file is selected when you press OK, the __DialogResult__ property will return True and the __FileName__ property will be set. You can use FileName to get the name of the selected file.

> Note that when the ShowDialog method is called the UI of the host application will freeze until the dialog closes.

#### __[C#] Example 1: Show a save file dialog__
{{regiond radfiledialogs-radsavefiledialog-0}}
	RadSaveFileDialog saveFileDialog = new RadSaveFileDialog();	
	saveFileDialog.Owner = theHostWindowInstance;	
	saveFileDialog.ShowDialog();
	if (saveFileDialog.DialogResult == true)
	{
		string selectedFileName = saveFileDialog.FileName;
	}
{{endregiond}}

## Creating a stream for the selected file

You can open a read-write file stream for the selected file using the __OpenFile__ method. Or alternatively you can use the FileName property and open the file manually.

#### __[C#] Example 2: Open a file stream__
{{regiond radfiledialogs-radsavefiledialog-1}}
	RadSaveFileDialog saveFileDialog = new RadSaveFileDialog();	
	saveFileDialog.Owner = theHostWindowInstance;	
	saveFileDialog.ShowDialog();
	if (saveFileDialog.DialogResult == true)
	{
		Stream fileStream = saveFileDialog.OpenFile();
	}
{{endregiond}}

## Working with the selected file

You can get the path of the selected file via the __FileName__ property (see __Example 1__). Note that the property is empty until the DialogResult is valid. When the dialog closes and if DialogResutl is True the property will return the corresponding file path.

The __FileName__ property can be set manually. This will change the value displayed in the selected file autocomplete box area. Note that setting this won't change the selected item in the list with the files.

#### __[C#] Example 3: Set the file name__
{{regiond radfiledialogs-radsavefiledialog-2}}
	RadSaveFileDialog saveFileDialog = new RadSaveFileDialog();	
	saveFileDialog.Owner = theHostWindowInstance;	
	 saveFileDialog.InitialDirectory = @"C:\Program Files\Internet Explorer\";
	saveFileDialog.FileName = @"C:\Program Files\Internet Explorer\filetosave.txt";
	saveFileDialog.ShowDialog();
{{endregiond}}

#### __Figure 2: Setting the file name__
![](images/radsavefiledialog-02.png)	

## See Also
* [Visual Structure]({%slug radfiledialogs-visual-structure%})
* [RadOpenFileDialog]({%slug radfiledialogs-radopenfiledialog%})
* [RadOpenFolderDialog]({%slug radfiledialogs-radopenfolderdialog%})
* [Events]({%slug radfiledialogs-events%})