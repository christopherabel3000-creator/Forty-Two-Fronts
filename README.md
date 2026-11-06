# Forty-Two Fronts

A turn-based world conquest game built for screen readers first. Play online with up to five friends, against the computer, or by passing one device around, on the classic 42-territory, six-continent world.

**Play:** https://christopherabel3000-creator.github.io/Forty-Two-Fronts/

## Accessibility

- Every choice is a plain button that reads in full, for example "Brazil, 5 armies. Enemy neighbors: North Africa (Computer 1, 2)."
- Dice results, captures and computer turns are spoken through live regions, and focus moves to the next step on its own.
- The whole board can be browsed as a list by continent, with each territory's owner, armies and neighbors.
- Sighted players can turn on a board diagram showing owners, army counts and connections.

## Online play

Choose “Online with a friend”, pick how many friends (1 to 5) and computer players (up to 6 players in all), and share the 4-letter code. The game starts when every seat is filled, or the host can start early with computers in the open seats. Every move is announced on every player's device.

Games are saved in the shared Firebase Realtime Database under `fortyTwoFronts/<CODE>`, separate from the other games' sections. The database only accepts a save whose version number is exactly one higher than the stored one, so two devices can never overwrite each other. `firebase-rules-section.json` holds this game's section, to be added alongside the other games' sections in the database rules.

## Setting up the board

Choose how the board is set up when you start a game:

- **Classic (3 to 6 players):** take turns claiming one empty territory at a time until all 42 are taken, then take turns placing the rest of your armies one at a time. Starting armies: 35 each for 3 players, 30 for 4, 25 for 5, 20 for 6.
- **Official two-player rules:** territories are dealt three ways, 14 to each player and 14 to a neutral army. Each side has 40 armies. On each setup turn you place 2 of your own armies and 1 neutral army. The neutral army never attacks, only defends, and you win by beating your opponent even if neutral territories remain.
- **Deal territories (3 to 6 players):** territories are dealt at random, then you take turns placing armies.
- **Quick start:** territories and armies are all dealt at random (two-player games still include the neutral army).

## How a turn works

1. **Place armies:** one for every three territories you hold (at least three), plus continent bonuses: Asia 7, North America 5, Europe 5, Africa 3, South America 2, Australia 2.
2. **Attack** from any territory with at least 2 armies. You roll up to 3 dice and the defender rolls up to 2. Ties go to the defender.
3. **Fortify:** make one move between connected territories you hold.

Capture a territory in a turn to earn a card. Trade sets of three for growing numbers of armies.

## Files

- `index.html`: the whole game in one file, with no build step.
- `firebase-rules-section.json`: this game's section of the Firebase Realtime Database rules.
