I had been having trouble with getting `ListFragment` working in Kotlin.  When the automatic "Convert Java code to Kotlin" in IntelliJ was invoked, the app would crash.

The original Java is:
```Java
@Override
public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)
```
The Kotlin plugin converts it to:
```kotlin
override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle): View?
```
Eventually I tracked this error down and it should be:
```kotlin
override fun onCreateView(inflater: LayoutInflater, container: ViewGroup?, savedInstanceState: Bundle?): View
```
Only `container` and `savedInstanceState` should be nullable, other combinations will cause a crash.
