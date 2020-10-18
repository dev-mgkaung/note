# In App Review Code snippet

## Dependencies
```python
 // This dependency is downloaded from the Google’s Maven repository.
    // So, make sure you also include that repository in your project's build.gradle file.
    implementation 'com.google.android.play:core:1.8.2'
    // For Kotlin users also import the Kotlin extensions library for Play Core:
    implementation 'com.google.android.play:core-ktx:1.8.1'

```

## Code Snippet
```python
 val manager = ReviewManagerFactory.create(this)
        val request = manager.requestReviewFlow()
        request.addOnCompleteListener { request ->
            if (request.isSuccessful) {
                // We got the ReviewInfo object
                val reviewInfo = request.result
                val flow = manager.launchReviewFlow(this, reviewInfo)
                flow.addOnCompleteListener { _ ->
                    // The flow has finished. The API does not indicate whether the user
                    // reviewed or not, or even whether the review dialog was shown. Thus, no
                    // matter the result, we continue our app flow.
                    Toast.makeText(this,"Success ", Toast.LENGTH_LONG).show()
                }
            } else {
                // There was some problem, continue regardless of the result.
                Toast.makeText(this," There was some problem, continue regardless of the result", Toast.LENGTH_LONG).show()
            }

```
