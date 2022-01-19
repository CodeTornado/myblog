

物体平缓向前移动

```c#
transform.Translate(Vector3.forward * Time.deltaTime * speed);
```





简易的镜头跟随

```c#

    public Vector3 offset = new Vector3(0, 5, -7);
    public GameObject playerObj;
    void LateUpdate()
    {
        this.transform.position = playerObj.transform.position + offset;
    }
```

