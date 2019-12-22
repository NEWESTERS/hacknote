# Управление состоянием

## State

### React

```tsx
import React, { FC, useState } from 'react'

const Counter: FC = () => {
    const [ count, setCount ] = useState(0)

    const increment = () => {
        setCount(count => count + 1)
    }

    return (
        <div>
            <p>Count: { count }</p>

            <button
                onClick={increment}
            >Increment</button>
        </div>
    )
}
```

### SwiftUI

```swift
import SwiftUI

struct Counter: View {
    @State var count = 0

    func increment() {
        count += 1
    }

    var body: some View {
        VStack {
            Text("Count: " + String(count))

            Button(action: increment) {
                Text("Increment")
            }
        }
    }
}
```
