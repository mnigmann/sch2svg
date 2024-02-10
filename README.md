# sch2svg
This tool is a Python program for converting gEDA gschem schematic files (.sch) and symbol files (.sym) to Scalable 
Vector Graphics (SVG) files. Custom symbol libraries, custom colors, and grid lines can be set with command line 
arguments. A full description of the gEDA gschem file format can be found at http://wiki.geda-project.org/geda:file_format_spec.

## Features
 * Can export both schematic (.sch) and symbol (.sym) files
 * Automatically identifies the bounds of the schematic
 * Colors can be configured by specifying a color configuration file at the command line
 * A minimum thickness can be set for lines to make them more visible when zoomed out

## Unsupported features
 * Does not support embedded images

## Colors
In the gEDA file format, colors are specified by an index. Each index relates to a particular function or feature. For
example, color index 1 is used for pins and color index 4 is used for nets. By default, the colors produced in the SVG
file are the same colors as rendered by gschem. However, if a different color scheme is needed, it may be specified with
a color configuration file. Each line in the color configuration file defines one color with a hexadecimal color code. 
Each color may be followed by a label or comment, as in the example configuration file, but note that it is not the 
contents of the label that determine the function of the color, but the order in which the colors occur in the file. An
example file, `light_colors.txt`, is provided. This color scheme is better suited to producing images for printing, since
it uses a white background rather than a black background.

## Usage
```
usage: sch2svg.py [-h] -i IN_FILE [-o OUT_FILE] [--colors COLORS] [-g] [-G] [-l [LIB ...]] [-t THICK]

Convert a gEDA/gschem schematic file (.sch) or symbol file (.sym) to an .svg image file

optional arguments:
  -h, --help            show this help message and exit
  -i IN_FILE, --in-file IN_FILE
                        A .sch or .sym file from which a schematic is read
  -o OUT_FILE, --out-file OUT_FILE
                        A .svg file to which an image of the schematic is written
  --colors COLORS       A file containing a list of colors
  -g                    Include minor grid lines every 100px
  -G                    Include major grid lines every 500px
  -l [LIB ...], --lib [LIB ...]
                        Directories to be recursively searched for symbol files
  -t THICK, --thick THICK
                        Minimum thickness of lines
```
