[go to README](../README.md).

# generate new yaml files


The code used to generate the input method files is in this project:
https://github.com/Weiqifan1/cjk-double-stroke-scala

The project is written in Scala-3 and generates .yaml files to be used with the
RIME input method engine.

To generate the .yaml files yourself, clone the project cjk-double-stroke-scala,
uncomment the test code in this file:
https://github.com/Weiqifan1/cjk-double-stroke-scala/tree/master/src/test/scala/GenerateOutput
and run it.
This will generate a number of .yaml files into the GenerateOutput folder
Take the matching .dict.yaml and .schema.yaml files and paste it
into you local rime folder. Then edit your preexisting default.custom.yaml
file as needed.
