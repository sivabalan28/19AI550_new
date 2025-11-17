# Ex.No: 10  Implementation of 2D Shooter Game – Space Invaders
### DATE:                                                                            
### REGISTER NUMBER : 21222240100 
### AIM: 
To develop a 2D Shooter Game (Space Invaders) in Unity using player shooting mechanics, enemy movement patterns, and collision-based gameplay.
### Algorithm:
```
1. Create a new Unity 2D project.
2. Add Player, Invader, Projectile, MysteryShip, and Bunker GameObjects to the scene.
3. Create prefabs for Player, Invaders, Laser Projectile, Mystery Ship, and Bunkers.
4. Add a Player script to control horizontal movement and shooting mechanics.
5. Add an Invader script to animate enemies and handle collision.
6. Add an Invaders controller script to move the entire enemy group left, right, and downward.
7. Add a Projectile script for upward (player) and downward (enemy) laser movement.
8. Add a MysteryShip script to periodically move the special enemy across the screen.
9. Add a GameManager script to track lives, score, and game-over state.
10. Use colliders and rigidbody2D components to detect hits between lasers, invaders, bunkers, and the player.
11. Test the game and ensure enemies get faster as the number of invaders decreases.

```  
### Program:
#### Player.cs
```
using UnityEngine;

public class Player : MonoBehaviour
{
    public Projectile laserPrefab;
    public float speed = 5f;
    private bool laserActive;

    void Update()
    {
        float movement = Input.GetAxis("Horizontal");
        transform.position += new Vector3(movement * speed * Time.deltaTime, 0f, 0f);

        if (Input.GetKeyDown(KeyCode.Space) && !laserActive)
        {
            Shoot();
        }
    }

    private void Shoot()
    {
        Projectile projectile = Instantiate(laserPrefab, transform.position, Quaternion.identity);
        projectile.SetDirection(Vector3.up);
        laserActive = true;
    }

    public void LaserDestroyed()
    {
        laserActive = false;
    }
}
```
#### Invader.cs
```
using UnityEngine;

public class Invader : MonoBehaviour
{
    public System.Action killed;

    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.gameObject.TryGetComponent(out Projectile projectile))
        {
            this.killed?.Invoke();
            Destroy(gameObject);
        }
    }
}

```
#### Projectile.cs
```
using UnityEngine;

public class Projectile : MonoBehaviour
{
    public float speed = 5f;
    private Vector3 direction;

    public void SetDirection(Vector3 dir)
    {
        direction = dir;
    }

    void Update()
    {
        transform.position += direction * speed * Time.deltaTime;
    }

    private void OnTriggerEnter2D(Collider2D collision)
    {
        Destroy(gameObject);

        if (collision.TryGetComponent(out Player player))
        {
            player.LaserDestroyed();
        }
    }
}
```
#### MysteryShip.cs
```
using UnityEngine;

public class MysteryShip : MonoBehaviour
{
    public float speed = 3f;

    void Update()
    {
        transform.position += Vector3.right * speed * Time.deltaTime;
    }
}
```
#### GameManager.cs
```
using UnityEngine;

public class GameManager : MonoBehaviour
{
    public int lives = 3;
    public int score = 0;

    public void AddScore(int value)
    {
        score += value;
    }

    public void LoseLife()
    {
        lives--;
    }
}
```
### Output:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/431e8187-4d39-4645-93bf-cda25070d01e" />
<img width="1919" height="1064" alt="image" src="https://github.com/user-attachments/assets/79d32b9a-0bd0-45d1-a64a-b0b94f4e45e3" />


### Result:
Thus, the 2D Shooter Game (Space Invaders) was successfully developed and implemented using Unity.
