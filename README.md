# P2: Tournament Results 

## Project Overview

This is the second project on Udacity's Full Stack Nanodegree program.

### Brief

Write a Python module that uses the PostgreSQL database to keep track of players and matches in a game tournament.

The game tournament will use the Swiss system for pairing up players in each round: players are not eliminated, and each player should be paired with another player with the same number of wins, or as close as possible.

This project has two parts: defining the database schema (SQL table definitions), and writing the code that will use it.

## Delivery

Python module that uses the PostgreSQL database to keep track of players and matches in a game tournament. Including:

- tournament.sql
- tournament.py

### Dependancies
- [Python](https://www.python.org/downloads/) 
- [Vagrant](http://vagrantup.com/)
- [VirtualBox](https://www.virtualbox.org/)
- [fullstack-nanodegree-vm repository](http://github.com/udacity/fullstack-nanodegree-vm)

### Usage
- Launch the Vagrant VM
- In order to run the tournament_test.py, you'll need to do the following:
-- $ psql
-- => create database tournament;
-- => \c tournament
-- => \i tournament.sql
-- => \q
-- $ python tournament_test.py

### Functions in tournament.py

####registerPlayer(name)

Adds a player to the tournament by putting an entry in the database. The database should assign an ID number to the player. Different players may have the same names but will receive different ID numbers.

####countPlayers()

Returns the number of currently registered players. This function should not use the Python len() function; it should have the database count the players.

####deletePlayers()

Clear out all the player records from the database.

####reportMatch(winner, loser)

Stores the outcome of a single match between two players in the database.

####deleteMatches()

Clear out all the match records from the database.

####playerStandings()

Returns a list of (id, name, wins, matches) for each player, sorted by the number of wins each player has.

####swissPairings()

Given the existing set of registered players and the matches they have played, generates and returns a list of pairings according to the Swiss system. Each pairing is a tuple (id1, name1, id2, name2), giving the ID and name of the paired players. For instance, if there are eight registered players, this function should return four pairings. This function should use playerStandings to find the ranking of players.

### Tables / View in tournament.sql

players:
- id serial primary key
- name text

match:
- winner integer references players(id)
- loser integer references players(id)

VIEWS

player_standings:
- id
- name
- wins
- matches


