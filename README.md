# CinemaLib

## Installation
Just clone repo into CinemaLib folder:

`git clone https://github.com/JonasLukasczyk/CinemaLib CinemaLib`

## Notebook Example
```
# IMPORTANT: CinemaLib repo must be in python path or in project directory
import CinemaLib

# Open Cinema Database
cdb  = CinemaLib.DatabaseReader();
cdb.inputs["Path"].setValue( 'Path To Cinema Spec D Database with jpg images' );

# Select Some Data Products
query = CinemaLib.DatabaseQuery();
query.inputs["Table"].setValue(cdb.outputs['Table']);
query.inputs["Query"].setValue('SELECT * FROM input LIMIT 5 OFFSET 0');

# Read Data Products
imageReader = CinemaLib.ImageReader();
imageReader.inputs["Table"].setValue(query.outputs['Table']);

# Render Images in Black and White (to demo shader effects)
imageRenderer = CinemaLib.ImageRenderer();
imageRenderer.inputs["Image"].setValue( imageReader.outputs["Images"] );

# Display Results
from IPython.display import display
images = imageRenderer.outputs["Image"].getValue();
for i in images:
    display(i)
```
