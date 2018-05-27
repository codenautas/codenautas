# Visual Studio Code en Codenautas

## settings

Las opciones que siguen normalmente están en `c:\users\NOMBRE\AppData\Roaming\Code\User\settings.json` y se puede acceder desde el menú principal `File -> Preferences -> Settings` o con las teclas <kbd>CTRL</kbd>+<kbd>,</kbd>

```json
{
    "git.autofetch": true,
    "extensions.ignoreRecommendations": false,
    "workbench.colorTheme": "Default Light+",
    "bash-terminal.integrated.shell.windows": "c:\\Program Files\\Git\\bin\\bash.exe",
    "terminal.integrated.shell.windows": "C:\\WINDOWS\\System32\\cmd.exe",
    "git.promptToSaveFilesBeforeCommit": true,
    "window.title": "${rootName}${dirty}${separator}${activeEditorShort}",
    "window.zoomLevel": 0
}
```

## teclas

Se pueden cambiar, por ejemplo se pueden usar las de **Notepad++**, para eso hay que instalar la extensión **Notepad++ keymap** (que no le funciona bien el <kbd>CTRL</kbd>+<kbd>D</kbd>, para eso hay que instalar otra extensión más: **Contextual Duplicate** y cambiar la tecla

Para cambiar las teclas la asignación está en `c:\users\NOMBRE\AppData\Roaming\Code\User\keybindings.json` se puede entrar: 

```json
[
    {
        "key": "ctrl+d",
        "command": "lafe.duplicateCode",
        "when": "editorTextFocus"
    }
]
```

## extensiones

  * Recomendadas:
    * **Notepad++ keymap** para tener las mismas teclas del notepad++
    * **Contextual Duplicate** para duplicar la línea o lo seleccionado (como hace el notepad++). Cambiar las teclas para poder usar <kbd>CTRL</kbd>+<kbd>D</kbd> 
    * **Bookmarks** (para marcar líneas en el texto y poder ir hasta ahí): marca con <kbd>CTLR</kbd>+<kbd>ALT</kbd>+<kbd>K</kbd> y se mueve hacia atrás y adelante con las teclas que están al lado de la *K*: <kbd>CTLR</kbd>+<kbd>ALT</kbd>+<kbd>J</kbd> <kbd>CTLR</kbd>+<kbd>ALT</kbd>+<kbd>L</kbd>
    * **languaje-stylus** para poder ver bonito coloreado los archivos *.styl*
    
