---
title:  "How to store a Tetris board using only 27 words"
parent: "Tetris hand-held console summary"
nav_order: 1
---



# The block types and their encoding
![Block types](/media/block-types.png)

The classic Tetris we're all familiar with has seven block types. That means that every grid location on the board can have one of eight states, including no block at all. Eight is a serendipitous number, being a power of two. So just for fun I got to thinking how I could minimize the memory needed to store the board. If there are eight possible states for each grid location, then only three bits are needed to store its state.

Our board is ten columns wide, just like the original. If we use three bits per grid square, and ten grid squares per row, that means just 30 bits to store the entire row! An entire row of our game board could comfortably fit inside a single 32-bit word. I created a spreadsheet to help me plan out the bit structure of our rows. The images above and below are screenshots from that spreadsheet.

![Game board](/media/game-board.png)

The table above shows each bit of our game board array. Each row is a single 32-bit word. Each block type has a different 3-bit encoding, with an empty space being represented by three zeros. One of the tremendous upsides of this is that we can check if a row is empty with a single assembly instruction! 

![Display board](/media/display-board.png)

This is what the player would see based on the table above.

<!--
# Using the ```gameboard_t``` type

The implementation 
-->
