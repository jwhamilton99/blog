---
title: Reverse Engineering Wordle
date: 2022-02-04
author: me
layout: post
---

*Alternate Title: "Sucking the Fun Out of Everyone's Favorite Word Guessing Game"*

**Warning: This article contains Wordle spoilers for February 4th. Proceed at your own risk.**

So, I found a tweet yesterday (sorry to whoever wrote it, but there is no way in hell I'll ever find it in the endless sea of Wordle tweets) that basically said "hey, Wordle stores all its info locally! Check it out!"

This piqued my interest, and I started poking around. Lo and behold, everything was stored in **window.localStorage**. Some initial experimenting yielded some fun results:

![Left: A screenshot of Wordle saying "Hi there, get affirmations!"; Right: A screenshot of Wordle with the green squares arranged to form a happy face](/assets/images/posts/2022/02/04/experiments.png)

However, I wanted to see if I could put this to good use. I wanted to *break* Wordle¹. I present to you: the Wordle Solver bookmarklet.

![A video of me pressing a button on iOS Safari, which fills in the Wordle board with the correct word.](/assets/images/posts/2022/02/04/solver.gif)

There are five main parts to how this code works:

1. Getting the game board object (where all the current game state stuff is stored)
2. Getting the solution from the game board
3. Input the solution into the game
4. Telling the game you inputted 5 letters
5. Submitting the word

I'll walk you through these step-by-step, but all the code is [right here](https://gist.github.com/jwhamilton99/b9b50355490e41c147855a254c4442e5).

First, a note on how Wordle is actually structured. The game itself is actually contained in a **\<game-app\>** tag, which contains all the game information.

There are 3 interesting things here:

1. **boardState**, which contains the letters on the board
2. **evaluations**, which contains each letter's state of correctness (absent, present, or correct)
3. **solution**, which (you guessed it) is the solution to the day's board

Modifying the first 2 directly is what let me make the fun boards from above.

So first, I grab the **\<game-app\>** object (which I will refer to as **game**), so I can access all the game state information. Next, I use **game.addLetter()** to input **game.solution** into the board.

The thing with the **addLetter()** method is that it's meant to only be called with one letter. So while I do call it with the full string and it adds all five letters to the board, the game still thinks you've only inputted one letter. So that's why I manually set **game.tileIndex** to 5, which just tells the game that you actually inputted five letters. Lastly, I simply call **game.submitGuess()** which I doubt I need to explain.

When I originally tried to do this, I tried making an iOS Shortcut by using its "Run JavaScript on Web Page" action. However, it didn't like me trying to access **game**'s custom properties, so I took a trip back to 2010 and settled on a bookmarklet.

Every method used in this solver is straight from the game itself, no hacks. If you want the fun sucked out of this worldwide phenomenon, add this link to your bookmarks:

<h2><a href='javascript:(function() { if(window.location.host == "www.powerlanguage.co.uk" && window.location.pathname == "/wordle/") { let game = document.body.getElementsByTagName("game-app")[0]; if(game.gameStatus != "IN_PROGRESS") { window.alert("Game is already finished."); return; } game.addLetter(game.solution); game.tileIndex = 5; game.submitGuess(); } else { window.alert("You are currently not on the Wordle website."); } })();'>Wordle Solver</a></h2>

You should be able to right-click and add it to your bookmarks, but if you can't, you can copy that link and paste it into an existing bookmark. Open it on the Wordle page, and it'll solve it for you.

Enjoy!

1. *I don't actually want to break Wordle. Love the game Josh <3*