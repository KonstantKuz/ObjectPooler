﻿# **How to work with pooler in editor**
First you need to create pool or poolgroup asset.

![create](https://github.com/KonstantKuz/ObjectPooler/blob/master/TutorScreenshots/create.png)

Fill all properties.  
If use name as tag - after spawn object you can return it to pool using  
ObjectPooler.Instance.ReturnObject(gameObject, gameObject.name);  
If use autoreturn object will be returned to pool automatically after delay you set.  

![pool](https://github.com/KonstantKuz/ObjectPooler/blob/master/TutorScreenshots/pool.png)

If you need to spawn some objects random or weighted random use pool groups.  
Create pools for all objects you need, create pool group asset and assign to it all pools, set group tag.  
Set all weights if you need - objects with higher weight will spawn more often. 

![group](https://github.com/KonstantKuz/ObjectPooler/blob/master/TutorScreenshots/group.png)

Last step in work in editor - assign all pools and groups to pooler.  
All pools in pool groups assets will be assigned automatically.  

![poolerEditor](https://github.com/KonstantKuz/ObjectPooler/blob/master/TutorScreenshots/poolerEditor.gif)

# **Code examples**

```C#
    private string objectTag = "Cube";
    private string groupTag = "Cubes";
    
    public void Example()
    {
        // Spawning objects by tag
        GameObject spawnObject = ObjectPooler.Instance.SpawnObject(objectTag);
        // overrides
        ObjectPooler.Instance.SpawnObject(objectTag, transform.position);
        ObjectPooler.Instance.SpawnObject(objectTag, transform.position, transform.rotation);

        // Spawning random objects by group tag
        GameObject randomObject = ObjectPooler.Instance.SpawnRandomObject(groupTag);
        // overrides
        ObjectPooler.Instance.SpawnRandomObject(groupTag, transform.position);
        ObjectPooler.Instance.SpawnRandomObject(groupTag, transform.position, transform.rotation);

        // Spawning weighted random objects by group tag
        GameObject randomWeightedObject = ObjectPooler.Instance.SpawnWeightedRandomObject(groupTag);
        // overrides
        ObjectPooler.Instance.SpawnWeightedRandomObject(groupTag, transform.position);
        ObjectPooler.Instance.SpawnWeightedRandomObject(groupTag, transform.position, transform.rotation);
        
        // Return object to pool
        ObjectPooler.Instance.ReturnObject(gameObject, objectTag);
        ObjectPooler.Instance.DelayedReturnObject(gameObject, objectTag, 1f);

        ObjectPooler.Instance.ReturnObject(gameObject, gameObject.name);
        ObjectPooler.Instance.DelayedReturnObject(gameObject, gameObject.name, 1f);
    }
```