<h1>Bonus</h1>
    
```swift

import SwiftUI

struct ContentView: View {
    let displayFontType = [".default", ".rounded", ".monospaced", ".serif"]
    @State var displayFontSelected = 0
    @State var isDeepScheme = false
    @State var colorArray: [Double] = [255.0, 255.0, 255.0]
    @State var stepperValue = 0
    @State var sliderValue = 0.0
    @State var selectedDate = Date() // Add this state for the selected date
    
    static let dateFormatter: DateFormatter = {
        let formatter = DateFormatter()
        formatter.dateFormat = "yyyy-MM-d"
        return formatter
    }()
    
    var body: some View {
        NavigationView {
            Form {
                Section(header: Text("字型設定")) {
                    Picker(selection: $displayFontSelected,
                           label: Text("字型選擇(\(displayFontSelected))")) {
                        ForEach(0..<displayFontType.count, id: \.self) {
                            Text(self.displayFontType[$0])
                        }
                    }
                }
                Section(header: Text("背景風格")) {
                    Toggle(isOn: $isDeepScheme) {
                        Text("深色(\(String(isDeepScheme)))")
                    }
                }
                Section(header: Text("計數器")) {
                    Stepper("Stepper(\(stepperValue))",
                            onIncrement: { stepperValue += 1 },
                            onDecrement: { stepperValue -= 1 })
                }
                Section(header: Text("滑桿(\(sliderValue, specifier: "%.2f"))")) {
                    Slider(value: $sliderValue, in: 0...1)
                }
                Section(header: Text("日期")) {
                    HStack{
                        Text(selectedDate, formatter: Self.dateFormatter)
                        DatePicker("", selection: $selectedDate, displayedComponents: .date)
                    }
                }
            }
            .navigationBarTitle("Settings 設定")
        }
    }
}

```
<img src="https://raw.githubusercontent.com/ctwoc111/yzu-swiftui-1101406/main/IMG_0067.jpg">
