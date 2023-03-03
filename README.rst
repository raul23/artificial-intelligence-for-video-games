=======================================
Artificial intelligence for video games
=======================================
Exploring and implementing AI algorithms for video games

.. contents:: **Contents**
   :depth: 5
   :local:
   :backlinks: top

Algorithms
==========
Coordinate action
-----------------
Flocking algorithm
""""""""""""""""""
TODO

Pathfinding
-----------
A*
""
Pseudocode
''''''''''
TODO

Books
=====
- `AI for Games, Third Edition (2020) by Ian Millington <https://www.amazon.com/AI-Games-Third-Ian-Millington/dp/0367670569>`_
- `Artificial Intelligence: A Modern Approach, 4th Edition (2020) by Stuart Russell and Peter Norvig 
  <https://www.amazon.com/Artificial-Intelligence-A-Modern-Approach/dp/0134610997>`_
- `Game AI Pro: Collected Wisdom of Game AI Professionals (2013) by Steve Rabin (editor) 
  <https://www.amazon.com/Game-AI-Pro-Collected-Professionals/dp/1466565969>`_
- `Game AI Pro 2: Collected Wisdom of Game AI Professionals (2015) by Steve Rabin (editor) 
  <https://www.amazon.com/Game-AI-Pro-Collected-Professionals/dp/1482254794>`_
- `Game AI Pro 3: Collected Wisdom of Game AI Professionals (2017) by Steve Rabin (editor)
  <https://www.amazon.com/Game-AI-Pro-Collected-Professionals/dp/1498742580>`_
- `Programming Game AI by Example (2004) by Mat Buckland <https://www.amazon.com/Programming-Example-Wordware-Developers-Library/dp/1556220782/>`_

Video lectures
==============
General
-------
MIT 6.034 Artificial Intelligence (Fall 2010)
"""""""""""""""""""""""""""""""""""""""""""""
`:information_source:`

 - **Playlist link:** `youtube.com <https://www.youtube.com/playlist?list=PLUl4u3cNGP63gFHB6xb-kVBiQHYe_4hSi>`_
 - 30 videos
 
   **Interesting videos:**
   
   - `5. Search: Optimal, Branch and Bound, A* <https://www.youtube.com/watch?v=gGQ-vAmdAOI&list=PLUl4u3cNGP63gFHB6xb-kVBiQHYe_4hSi&index=6>`_
   - `6. Search: Games, Minimax, and Alpha-Beta <https://www.youtube.com/watch?v=STjW3eH0Cik&list=PLUl4u3cNGP63gFHB6xb-kVBiQHYe_4hSi&index=7>`_
   - `Mega-R2. Basic Search, Optimal Search <https://www.youtube.com/watch?v=Tl_p5pgBsyM&list=PLUl4u3cNGP63gFHB6xb-kVBiQHYe_4hSi&index=26>`_
   - `Mega-R3. Games, Minimax, Alpha-Beta <https://www.youtube.com/watch?v=hM2EAvMkhtk&list=PLUl4u3cNGP63gFHB6xb-kVBiQHYe_4hSi&index=27>`_

UC Berkeley CS 188 Introduction to Artificial Intelligence (Fall 2018)
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
`:information_source:`
 
 - **Playlist link:** `youtube.com <https://www.youtube.com/playlist?list=PLsOUugYMBBJENfZ3XAToMsg44W7LeUVhF>`_
 - 25 videos
 
   **Interesting videos:**
   
   - `Search <https://www.youtube.com/watch?v=-Xx0QSFYfIQ&list=PLsOUugYMBBJENfZ3XAToMsg44W7LeUVhF&index=2>`_
   - `Informed Search <https://www.youtube.com/watch?v=Mlwrx7hbKPs&list=PLsOUugYMBBJENfZ3XAToMsg44W7LeUVhF&index=3>`_
   - `MDP <https://www.youtube.com/watch?v=4LW3H_Jinr4&list=PLsOUugYMBBJENfZ3XAToMsg44W7LeUVhF&index=8>`_
   - `RL <https://www.youtube.com/watch?v=TiXS7vROBEg&list=PLsOUugYMBBJENfZ3XAToMsg44W7LeUVhF&index=10>`_

Stanford CS221: Artificial Intelligence: Principles and Techniques (Autumn 2019)
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
`:information_source:`

 - **Playlist link:** `youtube.com <https://www.youtube.com/playlist?list=PLoROMvodv4rO1NB9TD4iUZ3qghGEGtqNX>`_
 - 19 videos
 
   **Interesting videos:**
   
   - `Search 1 - Dynamic Programming, Uniform Cost Search 
     <https://www.youtube.com/watch?v=aIsgJJYrlXk&list=PLoROMvodv4rO1NB9TD4iUZ3qghGEGtqNX&index=6>`_ 
   - `Search 2 - A* <https://www.youtube.com/watch?v=HEs1ZCvLH2s&list=PLoROMvodv4rO1NB9TD4iUZ3qghGEGtqNX&index=7>`_
   - `Markov Decision Processes 2 - Reinforcement Learning 
     <https://www.youtube.com/watch?v=HpaHTfY52RQ&list=PLoROMvodv4rO1NB9TD4iUZ3qghGEGtqNX&index=9>`_

Stanford CS221: Artificial Intelligence: Principles and Techniques (Autumn 2021) 
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
`:information_source:`

 - **Playlist link:** `youtube.com <https://www.youtube.com/playlist?list=PLoROMvodv4rOca_Ovz1DvdtWuz8BfSWL2>`_
 - 56 videos: they include videos from the semester Autumn 2019

Websites
========
Introduction to the A* Algorithm from Red Blob Games
----------------------------------------------------
`:information_source:`

 - **Link:** `redblobgames.com <https://www.redblobgames.com/pathfinding/a-star/introduction.html>`_
 - Created 26 May 2014, updated Aug 2014, Feb 2016, Jun 2016, Jun 2020
 - **Important:**
 
   - Which algorithm should you use for finding paths on a game map?

     "If you want to find paths from or to all all locations, use **Breadth First Search** or **Dijkstra’s Algorithm**. 
     Use Breadth First Search if movement costs are all the same; use Dijkstra’s Algorithm if movement costs vary.

     If you want to find paths to one location, or the closest of several goals, use **Greedy Best First Search** or A*. 
     Prefer A* in most cases. When you’re tempted to use Greedy Best First Search, consider using A* with an 
     “inadmissible” heuristic."
   - "I have lots more written about pathfinding `here <http://theory.stanford.edu/~amitp/GameProgramming/>`_. 
     Keep in mind that graph search is only one part of what you will need. A* doesn’t itself handle things like 
     cooperative movement, moving obstacles, map changes, evaluation of dangerous areas, formations, turn radius, 
     object sizes, animation, path smoothing, or lots of other topics."

    
