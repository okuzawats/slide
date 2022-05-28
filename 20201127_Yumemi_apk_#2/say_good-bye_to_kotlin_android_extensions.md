---
marp: true
theme: uncover
size: 16:9
paginate: true
headingDivider: 2
header: Say good-bye to Kotlin Android Extensions
footer: © 2020 okuzawats
---

# Say good-bye to Kotlin Android Extensions
okuzawats
YUMEMI.apk #2
2020/11/27
converted to markdown format 2022/05/28

<!--
_class: lead
_paginate: false
_header: ""
-->

## Who?

- okuzawats
  - Twitter: okuzawats
  - GitHub: okuzawats
- Android / Flutter（🆕）@ Fuller, Inc.

![bg right:50%](img/okuzawats.png)

## Kotlin 1.4.20-M2

Deprecate Kotlin Android Extensions compiler plugin

## Kotlin Android Extensions

- views
- parcelize

## Kotlin Android Extensions

- ~~views (dead)~~
- ~~parcelize (dead)~~

## views

_"not recommended practice"_

## Alternatives

- findViewById: traditional way
- ViewBinding: can use existing layout
- DataBinding: can bind variables in layout file

## Alternatives

- findViewById: traditional way
- **ViewBinding: can use existing layout**
- DataBinding: can bind variables in layout file

## Enable ViewBinding

```groovy
android {
  buildFeatures {
    viewBinding true
  }
}
```

## Enable ViewBinding

```kotlin
private var _binding: FragmentHomeBinding? = null
private val binding get() = requireNotNull(_binding)
```

## Enable ViewBinding

```kotlin
override fun onCreateView(
    inflater: LayoutInflater,
    container: ViewGroup?,
    savedInstanceState: Bundle?
): View? {
    _binding = FragmentHomeBinding.inflate(inflater, container, false)
    return binding.root
}
```

## Enable ViewBinding

```kotlin
override fun onDestroyView() {
    _binding = null
    super.onDestroyView()
}
```

## Enable ViewBinding

[wada811 / ViewBinding-ktx](https://github.com/wada811/ViewBinding-ktx)

```kotlin
private val binding: DataBindingFragmentBinding by dataBinding()
```

## Disable Kotlin Android Extensions (views)

```groovy
android {
   // ...
}

androidExtensions {
    features = ["parcelize"]
}
```

## Kotlin Android Extensions (parcelize)

```groovy
plugins {
    id 'kotlin-parcelize'
}
```

## Kotlin Android Extensions (parcelize)

```kotlin
import kotlinx.android.parcel.Parcelize
```

to

```kotlin
import kotlinx.parcelize.Parcelize
```

When update Kotlin 1.4.20-M2

##

Before:

```groovy
plugins {
  id 'kotlin-android-extensions'
}
```

After:

```groovy
plugins {
}
```

## Reference

- https://github.com/JetBrains/kotlin/releases/tag/v1.4.20-M2
- https://proandroiddev.com/migrating-the-deprecated-kotlin-android-extensions-compiler-plugin-to-viewbinding-d234c691dec7
