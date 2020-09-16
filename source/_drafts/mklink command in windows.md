## MKLINK [[/D] | [/H] | [/J]] Link Target

/D Creates a directory symbolic link. Default is a file symbolic link. /H Creates a hard link instead of a symbolic link. /J Creates a Directory Junction.

/D creates a symbolic link, or a soft link.This essentially acts like a shortcut to a folder in prior versions of Windows, except you don’t have to use an actual shortcut.

/H creates a hard link, which points directly to the file.This option can’t be used for folders directly for some reason, you’ll have to use the next option.

/J creates a “Directory Junction”A Directory Junction is actually just a hard link to a directory. This is a feature that existed prior to Vista as well. If you are trying to symlink to a directory using a hard link, then you should use this option.

Understanding Hard vs Soft Links

================================Hard Link

A hard link directly points to the file, and acts to the operating system as if it is the file itself. You’ll want to use this option the majority of the time if you are trying to fake an application’s directory.

Soft Link

A soft link is essentially a shortcut to a file or folder – if you are using Windows explorer, you’ll be redirected to the directory if you double-click on a shortcut, it won’t pretend its part of the filesystem. You can still directly reference or open a file with the symlinked path, and it mostly works.