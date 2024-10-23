# rime-liuma
劉碼輸入法 / 刘码输入法 / Liuma input: A shape-based input method for RIME IME

author: 劉可力 / 刘可力 c m l y k k e - h o t m a i l - c o m

## Usage
1. Edit and copy `default.custom.yaml` to your [RIME configuration directory](https://github.com/rime/home/wiki/RimeWithSchemata#rime-%E4%B8%AD%E7%9A%84%E6%95%B8%E6%93%9A%E6%96%87%E4%BB%B6%E5%88%86%E4%BD%88%E5%8F%8A%E4%BD%9C%E7%94%A8).
2. Scheme files for simplified Chinese is in `zmhans`, while traditional Chinese is in `zmhant`.

## Description
Release: 1.0 - 2024-10-16
First published 2024-10-16
劉碼 / 刘码 Liuma is a shape-based input method for typing chinese that you can learn in 10 minutes.
It contains 28.863 different single characters, and 179.226 multi-character words.
You can write any of the 5.000 most common characters without having to scroll,
using a maximum of 4 keystrokes per character (plus selection using the number keys).
It comes in to versions:
劉碼繁 Liumafan for writing traditional characters, and
刘码简 Liumajian for writing simplified characters.

This project is written in Scala-3 and generates .yaml files to be used with the 
RIME input method engine: 
https://rime.im/
https://github.com/rime

To generate the needed files, uncomment the 
test code in this file:
https://github.com/Weiqifan1/cjk-double-stroke-scala/tree/master/src/test/scala/GenerateOutput
and run it. 
This will generate a number of .yaml files into the GenerateOutput folder
Take the matching .dict.yaml and .schema.yaml files and paste it 
into you local rime folder. Then edit your preexisting default.custom.yaml
file as needed.

The complete .yaml files for Liuma version 1.0 can be found in this folder:
cjk-double-stroke-scala\src\v1_0

To see detailed information about the Liuma input method or how to configure RIME, 
go to the folder:
cjk-double-stroke-scala\src\info
