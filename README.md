I had been having trouble with getting `ListFragment` working in Kotlin.  When the automatic "Convert Java code to Kotlin" in IntelliJ was invoked, the app would crash.

Eventually I tracked this down to:
```kotlin
override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View
```
Only `container` and `savedInstanceState` should be nullable, other combinations will cause a crash.
