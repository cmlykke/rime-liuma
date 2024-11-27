[go to README](../README.md).

# Introduction

There are many shape-based input methods, 
so why create another one? Most existing methods take a long time to learn. 
However, they allow you to write any character without knowing its pronunciation, 
using only 4 keystrokes (e.g., 五笔字型 wubi [link](https://en.wikipedia.org/wiki/Wubi_method) 
or 郑码 zhengma [link](https://en.wikibooks.org/wiki/Zhengma_Input)) 
or 5 keystrokes (仓颉 cangjie [link](https://en.wikipedia.org/wiki/Cangjie_input_method)). 
Due to the difficulty of learning these methods, most people don't bother with them.

There has been at least two shape based methods that has been developed to be easy to learn:

五笔画 wubihua
https://en.wikipedia.org/wiki/Stroke_count_method

and 

六碼筆畫 g6code
http://www.miniapps.hk/g6code/

The problem with wubihua is that it often takes far too many keystrokes to write a single character,
as you can see here:
https://raw.githubusercontent.com/rime/rime-stroke/refs/heads/master/stroke.dict.yaml
for example, the code for the character 激 is "nnnpszhhnhzpphpn".
Often, you can get away with not typing that much, but on average it is still much more
than most people can stand in the long run.

g6code seems to be a solution to this. Each character is written with a maximum of 
6 keystrokes:
https://github.com/cyrus0880/rime-t9stroke/blob/main/rime-t9v1.3-uiojk/tnine.g6tc.dict.yaml
for eacmple, the code for 激 is jjuuoj.
So g6 is easy to learn, and has a reasonable maximum number of keystrokes.
However, the tradeoff is that you have a lot of collisions,
so when writing a code you often have to scroll past the first 9 candidate characters,
which is annoying and time-consuming.

# Liuma's attempt at a solution

First, the goal is to have a shape based input method that is easy to lean. 
Second, you should be able to write all or almost all common characters 
without having to scroll through a list of candidates.
For a RIME system, this means that there should be no more than 9 common characters
that share the same code.
Third, the maximum number of keystrokes needed to write a character should be low,
preferably no more than 4 like with Wubi and Zhengma.

Liuma attempt to solve this by having each key write two strokes.
All characters can be broken up into a list of 5 strokes:
horizontal 一, vertical 丨, left-slanted 丿, right-slanted 丶, and bent 乙.
If you take all possible two-stroke combinations of these, you get 25 (5*5)
possible combinations.
You can then have each key on the keyboard write a different 
two-stroke combination.

In Liuma, the combinations are placed such that 
combinations that start with the same strokes 
are put together on the same line, ordered with the horizontal stroke near the center, 
then vertical, left-slanted, right-slanted and bent stroke towards the sides of the keyboard, 
as you can see on the keyboard below:

![Liuma keyboard](../images/liumakeyboard-v1-2.png)

Even though this approach half's the amount of keystrokes
you need to write a character compared with Wubihua, to keep
the keystroke count low, it was still necessary to set a 
maximum number of strokes to write. Also, it is necessary to write both strokes from
the start and the end of the character. Therefore, in Liuma, you
type the first 6 strokes (3 letters) and the last two strokes 
(one letter) of the character you want to write.

# Simple Character examples

- 的 **UGKS** - first, you have a left-falling stoke (丿) followed by a vertical strokes (亅). 丿 strokes are on the 
keys y-p. Within the group, 一 is on y, 亅 is on u, so the first letter is **U**. Going to the next strokes in 白，
there is a bent stroke (乙) followed by a horizontal (一). 乙 strokes are on the keys a-g. Within the group, 一 is on g,
so the next letter is **G**. The final stroke of 白 is 一 and the first stroke of 勺 is 丿. The 一 strokes are on the 
keys h-m. Within the group, 一 is on h, 亅 is on j, 丿 is on k, so the next letter is **K**. 
You then go on to the last two strokes of 勺 which are 乙 (bent) and 丶(right-falling). 
The 乙 strokes are on the keys a-g and within the group 丶 is on the s key, so the final letter is **S**.
- 一 **H** - when you only have one stroke to write, you go to the relevant group (the 一 group on the letters h-m) 
and pick the key where the second stroke is the horizontal stroke. Therefore, the code for the character 一 is **H**, because it
is the 一 + 一 key. So the h key can write both the character 一 and the character 二.
- 是 **XHJO** - The first stroke is 亅 followed by 乙. 亅 strokes are on the keys x-n. Within the group, 一 is on n,
亅 is on b, 丿 is on v, 丶 is on c and 乙 is on x, so the first letter is **X**.
The next two strokes are 一 + 一 so the next letter is **H**.
The next two strokes of 是 are 一 + 亅. The 一 group is the letters h-m and within the group 亅 is on the j key,
so the next letter is **J**.
For the final letter, you write the last two strokes of the character which is 丿 + 丶.
丿 strokes are on the keys y-p. Within the group, 丶 is on o, so the final letter is **O**
- 不 **KC** - the strokes are 一 + 丿 + 亅 + 丶. within the 一 group, 丿 is on **K**, 
and withing the 亅 group, 丶 is on **C**, so the code becomes **KC** 
- 了 **F** - the strokes are 乙 + 亅 Within the 乙 group, 亅 is on **F**
so the code becomes **F**.

# The full characters displayed on the keyboard

As you can see from the keyboard, there are not just strokes but also characters listed:
On the top row: 馬車金糸言食門 and on the middle row: 虫木竹足目手.

Part of the goal of Liuma is that almost all common characters should be written
without scrolling. The most common 5.000 was chosen as the target.
This means that when ever you write a code, no character among the most
common 5.000 should be beyond the first 9 character options shown.
The most common 5.000 was picked as a target because it provided 
a good balance between coverage and the number of extra rules that needs to be menorized. 
If the target had been 6.000 or greater, Liuma would have been significantly harder to learn
without much extra benefit. Suppose you want to write characters among the 6.000
most common: 

For singlified characters and using Liumajian, these are the only characters
among the most common 6.000 where you have to scroll to see them when using the Liuma 4-codes:
(Using the frequency list here: https://lingua.mtsu.edu/chinese-computing/statistics/char/list.php?Which=MO)

- xhjo  題 5105, 嗉 5351,  
- jnho  聩 5209, 綦 5599,
- kxho  砹 5772, 硖 5856,
- ejoo  糇 5898,
- yhso  锿 5941,

Notice that the most common of these, 題, is the traditional form of 题. The character 题 can be written
without scrolling.

For traditional characters, using Liumafan, it looks like this:
(Using the frequency list here: http://technology.chtsai.org/charfreq/sorted.html)

- jnxo  鞅 5412, 顴 5454, 茦 5879,
- kxho  饜 5477, 戛 5769,
- xjgo  嘳 5724,
- xhjo  暪 5811,
- wjgo  漯 5821,

The approach of having each key stand for two strokes goes a long way to avoid character collisions,
but it was not enough to achieve the target of 5.000. For both simplified and traditional characters,\
there are too many that start with the following shapes/elements:

虫 木 ⺮ ⻊目 扌.

Therefore, six of the keys on the middle row have a dual purpose: 
they either stand for the two strokes like normal, or they 
stand for one of the six elements above.
For aesthetic reasons, I chose to also let the characters: 竹 足 手 be written
with the relevant keys as well as ⺮ ⻊and 扌.

Here are som examples:
- 蚜 **SMVZ**  - s here stands for 虫 rather than 乙 + 丶. **mv** stands for the 4 strokes in 牙. The **Z** at the end is added 
to the code to make the code four letters long.
- 棧 **DMEE** - d here stands for 木 rather than 乙 + 丿. **mee** stands for the first 4 and last 2 strokes in 戔.
- 筞 **FWGO** - f here stands for ⺮ rather than 乙 + 亅. **wgo** stands for the first 4 and last two strokes in 宋.
as you can see from 筞, when for example 木 occur later, it is not written with the **D** key.
Instead it is written with strokes as normal. Another example is 林 which is written **DJO** not **DD**.
- 跐 **JNND** - j here stands for ⻊ rather than 一 + 亅. **nnd** stands for the first 4 and last two strokes in 此
notice that the last shape 匕 can be written either as **D** 乙 + 丿 or as **M** 一 + 乙. 
So you could also write 跐 as jnnm if you want. Many characters can be written in different ways if the 
stroke order is not 100% clear.
- 眬 **KKDT** - k here stands for 目 rather than 一 + 丿. **KDT** stands for the 5 strokes in 龙. The letter **T** 
stands for the last 丶. This is because when you write only a single stroke, you use the letter that has 一 as is second
stroke. These are the keys T,Y,G,H and N.
- 揂 **LEJH** - l here stands for 扌 rather than 一 + 丶. **EJH** stands for the first 4 and last two strokes in 酋.

For traditional characters, there are even more such elements that create a large number of overlaps.
You can find the elements needed to write traditional characters on the top row of the keyboard.
Here are some examples that each follow the same pattern as described above:

駝 **WWAY**, 軛 **EKA**, 鉐 **RKXH**, 絀 **UFXN**, 諚 **IWGO**, 饀 **OIWH**, 閶 **PXHH**

# Avoiding the special elements

If you don't like these 13 special shapes/elements, you also have the option of 
writing characters without them. If you want to do that, 
you have to write the first 10 strokes of the character, plus the last two.
Here are the 7 traditional characters above, and the different ways they can be written with 6 letters:

- 駝 nhxwwp nhxwwd jhxwwp jhxwwd    
- 軛 jghnpg
- 鉐 ohcykg
- 絀 awwxxn awwfxn aroxxn arofxn
- 諚 thxlqo hhxlqo
- 饀 oqhsoh oqhsih oqhnkh omhsoh omhsih omhnkh
- 閶 xhxhxh

Overlaps for characters written with 6-codes:

Simplified:

There are now simplified characters in the frequency list where you have to scroll past the first 9 options.
The first character in the simplified frequency list where you have to scroll is pxjlwo 鯕 7522 (which actually is
the traditional version of 鲯) when using the frequency list here: https://lingua.mtsu.edu/chinese-computing/statistics/char/list.php?Which=MO:

Traditional:

For Traditional characters, using the 6-codes, these are the characters among the most common 6.000 where you have to scoll 
past the first 9 options when using the frequency list here: http://technology.chtsai.org/charfreq/sorted.html:

- jhxwwo / nhxwwo  騾 5168, 驃 5281, 騄 5405, 


# Multi-character words and phrases

Many shape based input methods offer the option of not just
writing individual characters, but whole words using relatively few keystrokes.
In liuma, you do that by following the pattern below, using the
characters 4-code. In order to write the multi-character words you therefore have to 
remember the 13 special shapes/elements.

All words are taken from the CC-Cedict open dictionary: https://www.mdbg.net/chinese/dictionary?page=cedict

## Two-character words: 
You write the first two strokes (one letter) and last two strokes (one letter)
of the first character, and the first four strokes (two letters) and last two strokes (one letter)
of the last character. In addition, 
all two-character words can also be written with just the first 3 letters.

Examples: 

- 你好  uodmn uod
- 泥孩  wmflo wdflo wpflo wmf wdf wpf
- 問話  pgiyg pgihg pgi 
(the first letter is p, because 門 is written with the p key, 
the third letter is i because 言 is on the i key)

## Three-character words:
You write the first two strokes of the first character, the first two and last two 
of the second character, and the first two and the last two strokes 
of the last character.

Examples:

- 主人翁  tooiz tootz
(here, the middle character is only written with two strokes, so the full code
is only 4 letters instead of 5. In such cases you write an extra z at the end)
- 啞巴虧  xfmnm
- CP值   zzuhz
(the first two letters is z because characters that doesn't consist of the five 
chinese strokes are written with z)

## Four-character words:
You write the first two strokes of the first three characters, and 
the first two and last two strokes of the last character.

Examples:

- 寶潔公司  wwogg
- 心砰砰跳  qkkjo
- 502胶    zzzpo

## Five-character words or more:
You write the first two strokes of the first five characters.

Examples:

- 中华人民共和国     xuogj
- 抗耐甲氧西林金葡菌  lkxyj
- 攻击型核潜艇       jhhdw
- 昆汀·塔伦提诺      xwzju
(just like numbers and letters of the alphabet, the · character doesn't consist of 
chinese strokes, so it is written with the letter z)
