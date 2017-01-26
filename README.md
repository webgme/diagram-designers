This repository contains the Panels, Controllers and Widgets making up the ModelEditor, SetEditor and Crosscut visualizers
from the generic UI.

The idea of this repository is to enable modifications of the aforementioned visualizers without the of keeping a fork
of webgme repo (which is a highly volatile), but instead forking off from this repo and import the visualizers
from that fork into your own domain repo.

Note that not all dependencies of the visualizers are checked in here. For instance the DragHelper is referred to at 
`'js/DragDrop/DragHelper'` (that is it's coming from the webgme-repo). In order to switch out components like this, 
you just change the path in your fork.

#### Using the visualizers
To import the visualizers from the particular repository (for a fork simple replace the webgme/diagram-designers with your
git repository) using [webgme-cli](https://github.com/webgme/webgme-cli).

Model Editor
```
webgme import viz ModelEditorDD webgme/diagram-designers
```

Set Editor
```
webgme import viz SetEditorDD webgme/diagram-designers
```

Crosscut
```
webgme import viz CrosscutDD webgme/diagram-designers
```

By default the ModelEditor from the webgme repository is the default visualizer to display. This can be changed by adding
the key-value-pair `"default": true` to the desired visualizer descriptor in your `src/visualizers/Visualizers.json`.

### Component Settings
By default the component-settings are the same as for the ones in the generic UI. However this can easily be changed by
changing the componentId (typically returned from `getComponentId()`) and any type of default configuration.


### How this repo is kept insync with webgme
When there are changes to any of the corresponding files in the webgme repo - these files need to be updated. Copy the 
entire folders and change the requirejs paths to point to `widgets/*` and `panels/*` from `js/Widgets/*` and `js/Panels/*`
where applicable.

We will make sure to maintain this repo at new webgme releases (at minimum).