---
layout: project
title: "Glaisher"
permalink: /projects/glaisher/
github: https://github.com/dmfrodrigues/feup-laig-proj/tree/master/TP3
try-it: https://dmfrodrigues.github.io/feup-laig-proj/TP3/
---

<div class="scroll" markdown="1">
![main menu](https://i.imgur.com/pxzskSJ.jpg)
![gameboard](https://i.imgur.com/MxQAUzl.jpg)
![room     ](https://i.imgur.com/lAuIWp5.jpg)
![alentejo ](https://i.imgur.com/IMdiVrQ.jpg)
![main menu](https://i.imgur.com/cOmDygK.jpg)
![gameboard](https://i.imgur.com/GVdGyJj.jpg)
</div>

A two-player board game where each player controls stacks of pieces.
Your goal is to conquer adversary stacks and connect opposing sides of the board with your stacks.
The main attraction is rather the 3D scenarios.

- **Environment:** WebGL, SICStus Prolog, Browser (Firefox/Chrome)
- **Tools:** Javascript, Prolog
- **Concepts:** autonomous player, user interface, 3D graphics, animation, shaders, texturing

This game uses WebGL (a 3D graphics framework for browsers), which by practical experience has much better performance on Chrome/Chromium than on Firefox.

The [game rules](https://nestorgames.com/rulebooks/GLAISHER_EN.pdf) were authored by Ken Shoda.  
Game design and rules by © 2015 Néstor Romeral Andrés and Ken Shoda.   
Implemented by [Diogo Rodrigues](https://github.com/dmfrodrigues) and [Breno Accioly](https://github.com/BrenoAccioly).  

## Technical details

The back-end is written in Prolog, [check it out on GitHub](https://github.com/dmfrodrigues/feup-plog-tp1). It is compatible with SICStus and SWI Prolog; the server is deployed at <https://feup-plog-tp1-staging.herokuapp.com> and is using SWI Prolog. Most of the code was developed in curricular unit [PLOG @FEUP](https://sigarra.up.pt/feup/en/ucurr_geral.ficha_uc_view?pv_ocorrencia_id=459482), but the server part was developed in curricular unit [LAIG @FEUP](https://sigarra.up.pt/feup/en/ucurr_geral.ficha_uc_view?pv_ocorrencia_id=459484).

The front-end is written in Javascript, with a bit of HTML/CSS; [see on GitHub](https://github.com/dmfrodrigues/feup-laig-proj/tree/master/TP3). It uses the interface library [WebCGF](https://paginas.fe.up.pt/~ruirodrig/pub/sw/webcgf/docs/) with some features we added, which in turn uses [WebGL](https://www.khronos.org/webgl/wiki/Main_Page). It was developed in curricular unit [LAIG @FEUP](https://sigarra.up.pt/feup/en/ucurr_geral.ficha_uc_view?pv_ocorrencia_id=459484).

## Rules

The game is played in a hexagonal board made of small hexagonal cells (called hexes); the board has a side of 5 hexes and a diagonal of 9 hexes.
The game is played using a set of 75 double-sided pieces, with one sided painted red and the other yellow. Player 1 is assigned color red, and player 2 color yellow.
The pieces may be stacked; all pieces in the same stack have the same color facing up, and a stack is owned by the player with the same color that the stack has facing up.

Each player starts with three 6-stacks (stacks of 6 pieces) in fixed positions in the board, as per the following figure.
<figure>
    <img alt="glaisher-start-board" src="https://raw.githubusercontent.com/dmfrodrigues/feup-plog-tp1/master/img/preparation.svg" style="width: 40%;"/>
</figure>

The players take turns, each turn being made of two actions:
1. **Split and move a stack**: choose a stack you own, and split it into different-size substacks (for instance, you can split a 6-stack into substacks [1,2,3] but not into substacks [3,3]). Then choose one of the six possible directions to move the substacks, and move each substack by as many cells as the stack is tall (i.e., a substack of size 2 will move 2 cells in the given direction). All pieces must land in hexes, otherwise they'd fall outside the board and the move would be illegal.
    - If a substack lands on a cell that already has a stack of the same player, the substack is placed on top of the existing stack;
    - If a substack lands on a cell that already has a stack of the other player:
    - If the existing stack is smaller or the same size as the substack the moving player conquers the enemy substack, by turning it around, and places his/her substack on top of that;
    - If the enemy stack is taller the move is illegal.
2. **Place a new piece**: choose an empty cell to place a new piece, grab a piece from the reserve and place it in that cell. The physical game comes with 75 pieces, but the rules do not impose restrictions on the height of stacks, and it is possible to accumulate more than 75 pieces on the board.

A player wins the game when he/she connects opposing sides of the game board with a contiguous chain of stacks of his/her color (the board has 6 sides), or when the opponent has no more valid moves. A cell in the gameboard corner is considered to belong to both sides of the board.
