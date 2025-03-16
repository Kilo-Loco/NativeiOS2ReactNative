# Native iOS to React Native Cheatsheet

## 🔹 Basics
| Swift / SwiftUI | React Native |
|----------------|--------------|
| `Int` | `number` |
| `String` | `string` |
| `Bool` | `boolean` |
| `Array<T>` | `T[]` |
| `Dictionary<Key, Value>` | `{ [key: string]: Value }` |
| `nil` | `null` or `undefined` |

## 🎨 UI Components
```swift
// SwiftUI
Text("Hello, world!")
```
```tsx
// React Native
<Text>Hello, world!</Text>
```

| Swift / SwiftUI | React Native |
|----------------|--------------|
| `Button` | `<Pressable>` / `<TouchableOpacity>` |
| `Image(systemName: "star")` | `<Image source={require('./star.png')} />` |
| `HStack` | `<View style={{ flexDirection: 'row' }}>` |
| `List {}` | `<FlatList />` |

## 🏗 State Management
```swift
// SwiftUI
@State private var count = 0
```
```tsx
// React Native
const [count, setCount] = useState(0);
```

| Swift / SwiftUI | React Native |
|----------------|--------------|
| `@Binding` | Prop + Callback |
| `@Published` | `useState` / `Context API` |

## 🔄 Navigation
```swift
// SwiftUI
NavigationLink(destination: DetailView()) {
    Text("Go to Details")
}
```
```tsx
// React Native (react-navigation)
onPress={() => navigation.navigate('Details')}
```

| Swift / SwiftUI | React Native |
|----------------|--------------|
| `NavigationView {}` | `Stack.Navigator` |
| `dismiss()` | `navigation.goBack()` |

## 🌐 Networking
```swift
// Swift URLSession
let url = URL(string: "https://api.example.com")!
let data = try await URLSession.shared.data(from: url)
```
```tsx
// React Native Fetch
const response = await fetch("https://api.example.com");
const data = await response.json();
```

## 🛠 Async / Await
```swift
// Swift Async Function
func fetchData() async -> Data {}
```
```tsx
// React Native Async Function
async function fetchData(): Promise<Data> {}
```

## 📦 Storage
| Swift / SwiftUI | React Native |
|----------------|--------------|
| `UserDefaults` | `AsyncStorage` |
| `Keychain` | `expo-secure-store` |

## 🏗 Animations & Gestures
```swift
// SwiftUI Animation
withAnimation {
    isExpanded.toggle()
}
```
```tsx
// React Native Reanimated
useSharedValue() + useAnimatedStyle()
```

## 📄 Models
```swift
// Swift Struct Model
struct User: Codable {
    let id: Int
    let name: String
    let email: String
}
```
```tsx
// React Native TypeScript Model
interface User {
    id: number;
    name: string;
    email: string;
}
```

## 🎨 Common UI Setups
### List of Objects
```swift
// SwiftUI List of Objects
struct User: Identifiable {
    let id: Int
    let name: String
}

struct UserListView: View {
    let users = [User(id: 1, name: "Alice"), User(id: 2, name: "Bob"), User(id: 3, name: "Charlie")]
    
    var body: some View {
        List(users) { user in
            Text(user.name)
        }
    }
}
```
```tsx
// React Native FlatList of Objects
interface User {
  id: number;
  name: string;
}

const users: User[] = [
  { id: 1, name: "Alice" },
  { id: 2, name: "Bob" },
  { id: 3, name: "Charlie" }
];

<FlatList 
  data={users} 
  keyExtractor={(item) => item.id.toString()} 
  renderItem={({ item }) => <Text>{item.name}</Text>} 
/>
```

## 📌 Swift Concepts to React Native
### Protocols
```swift
// Swift Protocol
protocol Animal {
    var name: String { get }
    func makeSound() -> String
}
```
```tsx
// React Native Interface
interface Animal {
    name: string;
    makeSound(): string;
}
```

### Enums
```swift
// Swift Enum
enum UserRole {
    case admin, user, guest
}
```
```tsx
// React Native Enum (TS)
enum UserRole {
    Admin = "admin",
    User = "user",
    Guest = "guest"
}
```

### Error Handling
```swift
// Swift Error Handling
enum MyError: Error {
    case invalidData
}

do {
    throw MyError.invalidData
} catch {
    print("Error: \(error)")
}
```
```tsx
// React Native Try/Catch
try {
    throw new Error("Invalid Data");
} catch (error) {
    console.error("Error:", error);
}
```

### Subclassing
```swift
// Swift Class Inheritance
class Animal {
    var name: String
    init(name: String) {
        self.name = name
    }
}

class Dog: Animal {
    func bark() {
        print("\(name) barks")
    }
}
```
```tsx
// React Native Class Inheritance
class Animal {
    name: string;
    constructor(name: string) {
        this.name = name;
    }
}

class Dog extends Animal {
    bark() {
        console.log(`${this.name} barks`);
    }
}
```

### Testing
```swift
// Swift XCTest
import XCTest

class MyTests: XCTestCase {
    func testExample() {
        XCTAssertEqual(1 + 1, 2)
    }
}
```
```tsx
// React Native Jest
import { render } from '@testing-library/react-native';
test('example test', () => {
    expect(1 + 1).toBe(2);
});
```

## Miscellaneous
| Swift / SwiftUI | React Native |
|----------------|--------------|
| `UIApplication.shared.open(URL)` | `Linking.openURL(url)` |
| `UIScreen.main.bounds` | `Dimensions.get('window')` |
