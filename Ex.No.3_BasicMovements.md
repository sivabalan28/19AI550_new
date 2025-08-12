# Ex.No: 3  Basic movements in Unity 
### DATE:  12-08-25                                                                          
### REGISTER NUMBER : 212222240100
### AIM: 
 To learn the basic movements translation,scaling and rotation of game objects through code.
### Procedure:
1. Setup the Scene
2. Open Unity and create a 3D Scene.
3. Add three objects:Cube → Rename to Object1 (for movement),Sphere → Rename to Object2 (for rotation).Capsule → Rename to Object3 (for scaling).
4. Add the Script,Create a C# Script → Name it TransformOperations.cs.
5. Write the code for translation,scaling and rotation,save and close the script
6. Save the script
7. Select any empty GameObject (or create one: GameObject → Create Empty).
8. Attach the TransformOperations script to it.
9. In the Inspector, assign Object1 → Drag the Cube,Object2 → Drag the Sphere.Object3 → Drag the Capsule.
10. Run the Scene Press Play ▶️ in Unity
11. Stop the program.
### Program 
```
using UnityEngine;
public class TransformOperations : MonoBehaviour
{
    public Transform object1; // Object for translation
    public Transform object2; // Object for rotation
    public Transform object3; // Object for scaling

    public float moveSpeed = 2f;  // Speed of translation
    public float rotateSpeed = 50f; // Speed of rotation
    public float scaleSpeed = 0.5f; // Speed of scaling

    void Update()
    {
        // Translate (Move) object1 along the X-axis- Time.deltaTime to make movement smooth across all frame rates
        if (object1 != null)
        {
           // object1.position += Vector3.right * moveSpeed;
               object1.Translate(0.02f,0,0);

        }

        // Rotate object2 around the Y-axis
        if (object2 != null)
        {
            //object2.Rotate(Vector3.up * rotateSpeed * Time.deltaTime);
            //object2.Rotate(0,0.02f.0);
        }

        // Scale object3 up and down
        if (object3 != null)
        {
           // float scaleChange = Mathf.PingPong(Time.time * scaleSpeed, 1f) + 0.5f; // generates a value that moves back and forth between 0 and length
           // object3.localScale = new Vector3(scaleChange, scaleChange, scaleChange);
            object3.localScale+=new Vector3(0.02f.0.02f,0);

        }
    }
}
```
```
using UnityEngine;

public class NewMonoBehaviourScript : MonoBehaviour
{
    public Transform o1;
    public Transform o2;
    public Transform o3;
    void Start()
    {


    }

    // Update is called once per frame
    void Update()
    {
        o1.Translate(0.2f,0,0);
        o2.Rotate(0.2f,0,0);
        o3.localScale+=new Vector3(0,0.02f,0);
    }
}
```

### Output:


<img width="1919" height="1079" alt="Screenshot 2025-08-12 144922" src="https://github.com/user-attachments/assets/9f8fbf1a-caf1-40ae-8467-6b64c73f4863" />
<img width="1919" height="1079" alt="Screenshot 2025-08-12 144935" src="https://github.com/user-attachments/assets/94c70820-532d-4973-9a06-dfad194977a0" />





### Result:
Thus the basic movement is learned through scripting


