# Introduction
---
To begin with, **Nostalgia** is a web version of the famous game *Piano Tiles*, Which grants you a flag if your score was 300 or above.

## Finding the Flag

After a successful account registration, we can navigate to the game we want to play, we notice after hitting exactly two tiles the game ends.
![[Files/Screenshot from 2025-08-20 20-23-29.png]]

After further investigation we can see a `POST` request is made to the server to update the user score to the actual score the user currently have.
we can see the `update_score.php` endpoint being called with the `POST` parameters below.
![[Screenshot from 2025-08-20 20-24-03.png]]

Inspecting the code given in the web page we have, we can see the function `generateHash()` that generates the hash value from above.
Given the said function, modifying the `score` value is not enough, the site refuses to update the `score` value.
![[Screenshot from 2025-08-20 20-24-52.png]]

An attempt is made to generate a new hash with the `score` value of 300, we can see a new `hash` value is made
![[Screenshot from 2025-08-20 20-26-40.png]]

We can now inject our newly created hash value and our modified score.
![[Screenshot from 2025-08-20 20-26-13.png]]

After sending the `POST` request we can see the server approves it and updates our score value immediately.
![[Screenshot from 2025-08-20 20-26-22.png]]

Finally we can see our flag is displayed at the bottom of the score board.
![[Screenshot from 2025-08-20 20-28-38.png]]