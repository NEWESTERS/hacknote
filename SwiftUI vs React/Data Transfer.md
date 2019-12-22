# Передача данных между компонентами

## Props

### React

```tsx
import React, { FC } from 'react'

interface IProps {
    text: string
}

const TextWrapper: FC<IProps> = ({ text }) => {
    return (
        <span>{ text }</span>
    )
}

const SampleComponent: FC = () => (
    <TextWrapper text="Hello, World!" />
)
```

### SwiftUI

```swift
import SwiftUI

struct TextWrapper: View {
    var text: String

    var body: some View {
        Text(text)
    }
}

struct SampleComponent: View {
    var body: some View {
        TextWrapper(text: "Hello, World!")
    }
}
```
