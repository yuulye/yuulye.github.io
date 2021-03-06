Project T -- Read me, like you've never read before
===

**note**: click the image for - Video Guide on YouTube

[![Video Guide on YouTube](https://img.youtube.com/vi/wTzeelhLw88/0.jpg)](https://youtu.be/wTzeelhLw88)

original sources:

  - [github.com/dwijpr/t](https://github.com/dwijpr/t): for commit histories, etc.
  - [core php.yuulye.github.io](https://github.com/yuulye/php.yuulye.github.io) + httrack
      - ``` $ git clone https://github.com/yuulye/yuulye.github.io```
      - copy yuulye.github.io folder ---> site
      - ``` $ httrack site```
      - ``` $ cd site```

original files for Project T (on refactor, still moving things)

```
index
`- t
    `- extra
    `- script
    `- style
```
------------------------------------

direct links:

- [index](https://github.com/yuulye/php.yuulye.github.io/blob/master/resources/views/game/t.blade.php)
- [extra](https://github.com/yuulye/php.yuulye.github.io/blob/master/resources/views/game/t/extra.blade.php)
- [script](https://github.com/yuulye/php.yuulye.github.io/blob/master/resources/views/game/t/script.blade.js); **note** - still very dirty
- [style](https://github.com/yuulye/php.yuulye.github.io/blob/master/resources/views/game/t/style.blade.css)


------------------------------------

## The Program Design / FlowChart / & Explanation

_Program Design_ -- a process that an organization uses to develop a program.

_FlowChart_ -- a diagram of the sequence of movements or actions of people or things involved in a complex system or activity.

_Explanation_ -- a statement or account that makes something clear. #sorry

## Flow Chart - App

### User

```
////^\\\\
      | ^   ^ |
     @ (o) (o) @
      |   <   |
      |  ___  |
       \_____/
     ____|  |____
    /    \__/    \
   /              \
  /\_/|        |\_/\
 / /  |        |  \ \
( <   |        |   > )
 \ \  |        |  / /
  \ \ |________| / /
   \ \|
```
[ASCII Art source](https://www.asciiart.eu/people/men)

---> Opens a Web Browser ---> Go to [Site](https://yuulye.github.io)
---> Click link [Project T](https://yuulye.github.io/game/t)
---> Play the Game!

### Game

```
Atari Controller
     []  ,----.___
   __||_/___      '.
  / O||    /|       )
 /   ""   / /   =._/
/________/ /
|________|/   dew
```
[ASCII Art source](https://www.asciiart.eu/computers/atari)

Atari ---> Nigiri (in Go/Baduk/Weiqi) [Play Go with me](https://online-go.com/player/588586/) / Randomize turn
---> player/AI turn

**Game Design** (Still part of Game Flow Chart)

```
+-----+ xs = [0];  +-----+ xs = [0]; +-----+ xs = [0,8]; +-----+ xs = [0,8];
|x| | |            |x| | | os = [4]; |x| | | os = [4];   |x|o| | os = [4,1];
| | | |            | |o| |           | |o| |             | |o| |
| | | |            | | | |           | | |x|             | | |x|
+-----+            +-----+           +-----+             +-----+

+-----+ xs = [0,8,6];  +-----+ xs = [0,8,6];
|x|o| | os = [4,2];    |x|o| | os = [4,1,7];
| |o| |                | |o| |
|x| |x|                |x|o|x|
+-----+                +-----+

Simple Map

0 1 2
3 4 5
6 7 8

### Sorted game records

```
xs = [0, 6, 8];
os = [1, 4, 7];
```
Comparing wins with sorted records after records have at least 3 pieces

Wins

// horizontals
[0,1,2],
[3,4,5],
[6,7,8],
// verticals
[0,3,6],
[1,4,7],
[2,5,8],
// diagonals
[0,4,8],
[2,4,6],

---> are there 3 connected pieces? 

`- no  ---> Play till death! (fill all 9 blocks) ---> [End]

`- yes ---> [End]

[End] ---> Restart? ---> backTo: [User]

```

## Additional Feature: Convos Battle!

tracking each other pieces as persons would...

```
+-----+                     
| | | | -----------------
| |x| | | enable convos |
| | | | -----------------
+-----+ 

+-----+ O : "What? Tengen!";
| | | | X : "Hahaha! Awesome right?";
| |x| | 
| | | | 
+-----+ 

+-----+ O : "What? Tengen!";
| | |o| X : "Hahaha! Awesome right?";
| |x| | O : "Alright... here I go, _San San_!";
| | | | X : "Naaaniii!??!;
+-----+ 

Still very buggy...

```

## The Game without AI

**note** - because it's the beautiful part...

```

[User] ---> Browser ---> Game ---> 'X' and 'O' Take Turn

---> Game check if:

      `---> there are 3 connected dots vertical, horizontal, diagonal

      `---> all the blocks is filled!

---> Game Restart menu ---> [User]

---------------------------------------

NOTE: Will not be available / be seen on latter version - just for development purpose.

```

## Artificial Intelligence

I am not sure about this, but let me try... 

## Dummy - AI

move #:
1. Random(first available)
2. Random(first available)
3. Random(first available)
4. Random(first available)
5. Random(first available)
6. Random(first available)
7. Random(first available)
8. Random(first available)
9. Random(first available)

## Jon - AI

move #:
1. Random(available)
2. Random(available)
3. Random(available)
4. Prevent enemy Win, Random(available)
5. Check game, Prevent enemy Win, Random(available)
6. Check game, Prevent enemy Win, Random(available)
7. Check game, Prevent enemy Win, Random(available)
8. Check game, Prevent enemy Win, Random(available)
9. Check game, Prevent enemy Win, Random(available)

-------

## Extra

### Possibility

This part I was going to use as building better AI but I will probably run out of time...

### Using Scoring System [not implemented]

```

From Wins we can get something like:  

horizontal                                                                       
[0,1,2],           0: 111  = 3                                                  
[3,4,5],           1: 11   = 2                                                  
[6,7,8],           2: 111  = 3                                                  
// vertical        3: 11   = 2                                                  
[0,3,6],           4: 1111 = 4,  #1 - for example                                 
[1,4,7],           5: 11   = 2                                                  
[2,5,8],           6: 111  = 3                                                  
// diagonal        7: 11   = 2                                                  
[0,4,8],           8: 111  = 3                                                  
[2,4,6],                                                                        
                                                                                
```

----------------------------------------------------------------------

**Error**

[repl.it](https://repl.it/@dwijpr/t)
unknown error, sometime it gives error ```500```

----------------------------------------------------------------------

<!-- Please don't remove this: Grab your social icons from https://github.com/carlsednaoui/gitsocial -->

<!-- display the social media buttons in your README -->

[![alt text][1.1]][1]
[![alt text][2.1]][2]
[![alt text][3.1]][3]
[![alt text][4.1]][4]
[![alt text][5.1]][5]
[![alt text][6.1]][6]


<!-- links to social media icons -->
<!-- no need to change these -->

<!-- icons with padding -->

[1.1]: http://i.imgur.com/tXSoThF.png (twitter icon with padding)
[2.1]: http://i.imgur.com/P3YfQoD.png (facebook icon with padding)
[3.1]: http://i.imgur.com/yCsTjba.png (google plus icon with padding)
[4.1]: http://i.imgur.com/YckIOms.png (tumblr icon with padding)
[5.1]: http://i.imgur.com/1AGmwO3.png (dribbble icon with padding)
[6.1]: http://i.imgur.com/0o48UoR.png (github icon with padding)

<!-- icons without padding -->

[1.2]: http://i.imgur.com/wWzX9uB.png (twitter icon without padding)
[2.2]: http://i.imgur.com/fep1WsG.png (facebook icon without padding)
[3.2]: http://i.imgur.com/VlgBKQ9.png (google plus icon without padding)
[4.2]: http://i.imgur.com/jDRp47c.png (tumblr icon without padding)
[5.2]: http://i.imgur.com/Vvy3Kru.png (dribbble icon without padding)
[6.2]: http://i.imgur.com/9I6NRUm.png (github icon without padding)


<!-- links to your social media accounts -->
<!-- update these accordingly -->

Your Google+ account is going away on April 2, 2019.

[1]: http://www.twitter.com/lyeyuu
[2]: http://www.facebook.com/yuulye
[3]: https://plus.google.com/102832888196813116163
[4]: http://yuulye.wordpress.com
[5]: http://dribbble.com/carlsednaoui
[6]: http://www.github.com/yuulye

<!-- Please don't remove this: Grab your social icons from https://github.com/carlsednaoui/gitsocial -->

//endOfFile readme.md
