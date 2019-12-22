# Базовые компоненты

## Render

### React

```tsx
import React, { FC, Fragment } from 'react'

const TwoLineHelloWorld: FC = () => {
    return (
        <Fragment>
            <span>Hello,</span>
            <span>World!</span>
        </Fragment>
    )
}
```

### SwiftUI

```swift
import SwiftUI

struct TwoLineHelloWorld: View {
    var body: some View {
        VStack {
            Text("Hello,")
            Text("World!")
        }
    }
}
```
