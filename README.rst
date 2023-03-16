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
Chess AI (TODO)
---------------
TODO

Flocking algorithm
------------------
In JavaScript: a port of Paul Roberts' C# implementation of flocking
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
.. raw:: html

   <div align="center">
    <a href="https://codepen.io/raul23/full/rNZwZVB" target="_blank">
      <img src="https://github.com/raul23/flocking-algorithms/blob/main/images/fullscreen.png">
    </a>
  </div>
  
- I ported a flocking algorithm implemented in C# code to JavaScript. The original author of the C# implementation
  is Paul Roberts and it is from the book `Artificial Intelligence in Games 
  <https://www.routledge.com/Artificial-Intelligence-in-Games/Roberts/p/book/9781032033228>`_.
- **JavaScript code:** 

  - `codepen.io <https://codepen.io/raul23/full/rNZwZVB>`_ (fullscreen; **Test it live!**)
  - `codepen.io <https://codepen.io/raul23/pen/rNZwZVB>`_ (source code)
- More information about this JavaScript port can be found on my GitHub page 
  `Flocking algorithms <https://github.com/raul23/flocking-algorithms>`_

.. Maze-solving algorithms (TODO)
.. ------------------------------
.. random mouse (TODO)
.. """""""""""""""""""
.. TODO

.. wall follower (TODO)
.. """"""""""""""""""""
.. TODO

.. Pledge algorithm (TODO)
.. """""""""""""""""""""""
.. TODO

Pathfinding
-----------
A*
""
Pseudocode
''''''''''
From the `Wikipedia article <https://en.wikipedia.org/wiki/A*_search_algorithm#Pseudocode>`_ about the A* search algorithm:

.. code-block:: javascript

   function reconstruct_path(cameFrom, current)
       total_path := {current}
       while current in cameFrom.Keys:
           current := cameFrom[current]
           total_path.prepend(current)
       return total_path

   // A* finds a path from start to goal.
   // h is the heuristic function. h(n) estimates the cost to reach goal from node n.
   function A_Star(start, goal, h)
       // The set of discovered nodes that may need to be (re-)expanded.
       // Initially, only the start node is known.
       // This is usually implemented as a min-heap or priority queue rather than a hash-set.
       openSet := {start}

       // For node n, cameFrom[n] is the node immediately preceding it on the cheapest path from the start
       // to n currently known.
       cameFrom := an empty map

       // For node n, gScore[n] is the cost of the cheapest path from start to n currently known.
       gScore := map with default value of Infinity
       gScore[start] := 0

       // For node n, fScore[n] := gScore[n] + h(n). fScore[n] represents our current best guess as to
       // how cheap a path could be from start to finish if it goes through n.
       fScore := map with default value of Infinity
       fScore[start] := h(start)

       while openSet is not empty
           // This operation can occur in O(Log(N)) time if openSet is a min-heap or a priority queue
           current := the node in openSet having the lowest fScore[] value
           if current = goal
               return reconstruct_path(cameFrom, current)

           openSet.Remove(current)
           for each neighbor of current
               // d(current,neighbor) is the weight of the edge from current to neighbor
               // tentative_gScore is the distance from start to the neighbor through current
               tentative_gScore := gScore[current] + d(current, neighbor)
               if tentative_gScore < gScore[neighbor]
                   // This path to neighbor is better than any previous one. Record it!
                   cameFrom[neighbor] := current
                   gScore[neighbor] := tentative_gScore
                   fScore[neighbor] := tentative_gScore + h(neighbor)
                   if neighbor not in openSet
                       openSet.add(neighbor)

       // Open set is empty but goal was never reached
       return failure

Implementation (JavaScript) [TODO]
''''''''''''''''''''''''''''''''''
TODO

Steering behaviors: Seek, Arrive, Flee, Avoidance, and Wander
-------------------------------------------------------------
In JavaScript: a port of Paul Roberts' C# implementation of all steering behaviors
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
.. raw:: html

   <div align="center">
    <a href="https://codepen.io/raul23/full/KKxQKzK" target="_blank">
      <img src="https://raw.githubusercontent.com/raul23/steering-behaviors/main/images/combining_fullscreen_with_options.png">
    </a>
    <p align="center">Green "zombies" wandering, flocking and avoiding obstacles including the user-controlled red "zombie"</p>
  </div>

**Description**

`:information_source:` 

 I ported the steering behaviors implemented in C# (+ Unity) code from Paul Roberts' 
 book `Artificial Intelligence in Games <https://www.routledge.com/Artificial-Intelligence-in-Games/Roberts/p/book/9781032033228>`_ to 
 JavaScript using the ``phaser.js`` 2D game development library.
 
**JavaScript port:** you can run the JavaScript code (which uses ``phaser.js``) through your browser via codepen.io

- `codepen.io <https://codepen.io/raul23/full/KKxQKzK>`_ (fullscreen; **Test it live!**)
- `codepen.io <https://codepen.io/raul23/pen/KKxQKzK>`_ (source code)
- `github.com <https://github.com/raul23/steering-behaviors/tree/main/code/combining>`_ (source code)

- The author used zombies invading a shopping mall in search of fresh brains as a backdrop for a simple game where you will
  implement and test different steering behaviors exhibited by the horde of zombies. 
  
  In the C# game, each zombie is represented as a green dot
  on the screen and can be spawned at specific places and at a certain rate during the game. The user controls a 
  black dot that can shoot at the zombies with the spacebar.
  
  .. raw:: html

      <div align="center">
       <a href="https://www.routledge.com/Artificial-Intelligence-in-Games/Roberts/p/book/9781032033228" target="_blank">
         <img src="https://raw.githubusercontent.com/raul23/flocking-algorithms/main/images/book_project.png">
       </a>
       <p align="center">From Paul Roberts' book <i>Artificial Intelligence in Games</i>, p.56</p>
      </div>
  
  `:information_source:` 
  
   - In the JavaScript port, green balls serve as a substitute for zombies.
   - Also for some of the steering behaviors, the user can control a red "zombie". For example, in the case of the 
     avoidance JavaScript implementation, 
     the user can move the red "zombie" anywhere on the canvas and the green "zombies" will try to avoid it like any other
     obstacles.
     
     .. raw:: html

         <div align="center">
          <a href="https://codepen.io/raul23/full/KKxQKzK" target="_blank">
            <img src="https://raw.githubusercontent.com/raul23/steering-behaviors/main/images/avoiding_red.png">
          </a>
          <p align="center">Green "zombies" avoiding the red "zombie" that can be controlled by the user</p>
         </div>
- Each steering behavior has an associated weight. These are the default values:

  - Arrive weight: 0.5
  - Avoidance weight: 0.75
  - Flee weight: 0.5
  - Flocking weight: 0.25
  - Seek weight: 0.5
  - Wander weight: 0.25
- The user can control a red "zombie" (.i.e. ball) with the arrow keys and can move it anywhere around the
  canvas so that the other green "zombies" can use it as a target to avoid or follow.
  
  In the case of the arrive behavior, 
  eventually they will cease all movement once they reach an
  equilibrium state where all green "zombies" will be piled on top of each other.
  
  .. raw:: html

      <div align="center">
       <a href="https://codepen.io/raul23/full/KKxQKzK" target="_blank">
         <img src="https://raw.githubusercontent.com/raul23/steering-behaviors/main/images/avoiding_covered_red.png">
       </a>
       <p align="center">The green "zombies" arrived at destination which is the <br/>user-controlled red "zombie" 
       that is completely covered by them.
     </div>
- More information about this project can be found at my GitHub page `Steering behaviors <https://github.com/raul23/steering-behaviors>`_

.. Swarm algorithms (TODO)
.. -----------------------
.. TODO

Articles
========
- Abd Algfoor, Zeyad; Sunar, Mohd Shahrizal; Kolivand, Hoshang (2015). `"A Comprehensive Study on Pathfinding 
  Techniques for Robotics and Video Games" <https://www.hindawi.com/journals/ijcgt/2015/736138/>`_. 
  International Journal of Computer Games Technology. 2015: 1–11. doi:10.1155/2015/736138.
- Hagelback, Johan, and Stefan J. Johansson. `"Dealing with fog of war in a real-time strategy game environment." 
  <https://ieeexplore.ieee.org/document/5035621>`_ In Computational Intelligence and Games, 2008. CIG'08. 
  IEEE Symposium On, pp. 55-62. IEEE, 2008.
- Lara-Cabrera, R., Nogueira-Collazo, M., Cotta, C., & Fernández-Leiva, A. J. (2015). 
  `Game artificial intelligence: challenges for the scientific community <https://ceur-ws.org/Vol-1394/paper_1.pdf>`_.
- Lidén, L. (2003). `Artificial stupidity: The art of intentional mistakes 
  <http://www.liden.cc/lars/WEB/Resume/Papers/2003_AIWisdom.pdf>`_. AI game programming wisdom, 2, 41-48.
  
   "During play-testing, it was discovered that occasionally when a player threw a
   grenade at a group of NPCs, Half-Life’s **pathfinding algorithm** was unable to find
   a path for all of the NPCs to escape. The behavior of remaining NPCs looked exceptionally 
   dumb as they shuffled around trying to find a way out. Rather than redesigning the pathfinding 
   system (a huge undertaking), Valve’s solution was to detect when
   the problem occurred and play **specialty animations** of the trapped marines crouching
   down and putting their hands over their heads. This was very well received by playtesters, 
   as it added to the character of the game."

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

    
