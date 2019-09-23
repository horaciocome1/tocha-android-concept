# tocha-android-concept
A android library that makes an easy and mantainable interface to tocha on android.
See what tocha is, and how to implement it on your back-end [here](https://github.com/rosariopfernandes/Tocha).

## Examples

```kotlin
val db = FirebaseFirestore.getInstance()
val collectionReference = db.collection("users")
collectionReference.searchWithTocha()    // for Java use Tocha.getInstance(collectionReference)
    .addField("name")
    .addField("bio")
    .searchFor("John", SearchOptions.startWith())
    .addSnapshotListener { snapshot, exception ->
        // handle snapshot of results collection
    }
```
OR you might want to add some options to the results:
```kotlin
val db = FirebaseFirestore.getInstance()
val collectionReference = db.collection("users")
collectionReference.searchWithTocha()    // for Java use Tocha.getInstance(collectionReference)
    .addField("name")
    .addField("bio")
    .searchFor("John", SearchOptions.startWith())
    .whereGreaterThanOrEqualTo("score", 0.8)
    .orderBy("score", Query.Direction.DESCENDING)
    .limit(15)
    .addSnapshotListener { snapshot, exception ->
        // handle snapshot of results collection
    }
```
