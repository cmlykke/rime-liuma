[go to README](../README.md).

# install on pc

Here is an english laguage guide to use rime on a pc (using the zhengma input method as an example):
https://wiki.michaelhan.net/Hanja_IME

After rime has been installed:

# Go to the folder rime-liuma\yamlFiles and download the files
# Edit and copy-paste `default.custom.yaml` 
Go to your [RIME configuration directory](https://github.com/rime/home/wiki/RimeWithSchemata#rime-%E4%B8%AD%E7%9A%84%E6%95%B8%E6%93%9A%E6%96%87%E4%BB%B6%E5%88%86%E4%BD%88%E5%8F%8A%E4%BD%9C%E7%94%A8). (this step is described in more detail in the english language guide above. It should be a folder like this: C:\Users\User\AppData\Roaming\Rime)

in my case it looks like this:

"""
customization:
distribution_code_name: Weasel
distribution_version: 0.14.3
generator: "Rime::SwitcherSettings"
modified_time: "Fri May  5 22:30:30 2023"
rime_version: 1.5.3
patch:
schema_list:
- {schema: zmhant}
- {schema: tnine}
- {schema: array30}
- {schema: cangjie5}
- {schema: cangjie6}
- {schema: cangjie6_express}
  """


add the Schema names to this file so it looks something like this:


"""
customization:
distribution_code_name: Weasel
distribution_version: 0.14.3
generator: "Rime::SwitcherSettings"
modified_time: "Fri May  5 22:30:30 2023"
rime_version: 1.5.3
patch:
schema_list:
- {schema: liumajian}
- {schema: zmhant}
- {schema: tnine}
- {schema: array30}
- {schema: cangjie5}
- {schema: cangjie6}
- {schema: cangjie6_express}
  """
# Copy and paste you desired .yaml files into the same folder
   (the two liumafan or the two liumajian files or all four)
Then restart the computer. 

# To change between configured input methods:
After restarting your PC, you can pres the WIN key + the SPACE key to change
your computer input to use RIME. After Rime is selected,
you can press F4 to change between the different RIME
methods. You should now see
劉碼繁 or 刘码简 among the options.

