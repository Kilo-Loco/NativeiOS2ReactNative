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
// SwiftUI List
struct UserListView: View {
    let users = ["Alice", "Bob", "Charlie"]
    
    var body: some View {
        List(users, id: \ .self) { user in
            Text(user)
        }
    }
}
```
```tsx
// React Native FlatList
const users = ["Alice", "Bob", "Charlie"];

<FlatList 
  data={users} 
  keyExtractor={(item) => item} 
  renderItem={({ item }) => <Text>{item}</Text>} 
/>
```

### Toggle / Switch
```swift
// SwiftUI Toggle
@State private var isOn = false

Toggle("Enable Feature", isOn: $isOn)
```
```tsx
// React Native Switch
const [isOn, setIsOn] = useState(false);

<Switch value={isOn} onValueChange={setIsOn} />
```

### Calendar
```swift
// SwiftUI DatePicker
DatePicker("Select Date", selection: $selectedDate, displayedComponents: .date)
```
```tsx
// React Native DatePicker (Using @react-native-community/datetimepicker)
import DateTimePicker from '@react-native-community/datetimepicker';
const [date, setDate] = useState(new Date());

<DateTimePicker value={date} mode="date" onChange={(event, newDate) => setDate(newDate || date)} />
```

## Miscellaneous
| Swift / SwiftUI | React Native |
|----------------|--------------|
| `UIApplication.shared.open(URL)` | `Linking.openURL(url)` |
| `UIScreen.main.bounds` | `Dimensions.get('window')` |
