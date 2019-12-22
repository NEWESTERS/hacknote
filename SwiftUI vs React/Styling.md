# Вёрстка

## Стили

### React

```tsx
import React, { FC } from 'react'

const AmazingText: FC = () => (
    <span
        style={{
            fontSize: "2em",
            color: "green"
        }}
    >Hello, World!</span>
)
```

### SwiftUI

```swift
import SwiftUI

struct AmazingText: View {
    var body: some View {
        Text("Hello, World!")
            .font(.title)
            .foregroundColor(.green)
    }
}
```
