 # Flag Command - HTB - Very Easy - Web

> Challenge: Dimensional Escape Quest by Xclow3n

## Overview
Text-based game where you wake up in a forest. All visible options kill you. Need to find hidden dev command.

## Steps to Solve

### 1. Initial Recon
- Connected to game server
- Typed help -> showed all dangerous commands like HEAD NORTH etc
- Tried them -> all result in death

### 2. Think Like a Developer
- Game must have hidden options not shown in help
- Checked page source (Ctrl+U) - nothing
- Opened DevTools (Right-click > Inspect)

### 3. Network Tab Discovery - THE KEY
- In DevTools > Network tab
- Typed start and triggered a command
- Saw request to /api/options
- Clicked on it > Response tab
- Scrolled to bottom - FOUND SECRET COMMAND at very end

### 4. Secret Command
1. Type start to reset game
2. Type exactly: Blip-blop, in a pickle with a hiccup! Shmiggity-shmack
3. Game says "You escaped the forest and won the game!"

### Flag
HTB{D3v310p3r_t0015_4r3_b35t__t0015_wh4t_d0_y0u_Th1nk??}

## Lesson Learned
Always check Network tab. Frontend should never receive secrets. DevTools are best tools!

## Fix
Server should filter dev-only commands and not send them in /api/options response. Use role-based filtering.
