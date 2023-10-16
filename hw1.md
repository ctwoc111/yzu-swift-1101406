<h1>HW1</h1>

```swift

import SwiftUI

struct ContentView: View
{
  var body: some View
  {
    Image("UserPhoto")
    .resizable()
    .aspectRatio(contentMode: .fit)
    .frame(width: 670, height: 670, alignment: .center)
    .overlay(
      Text("1101406 徐宇昕\nNo pain, no gain.")
      .fontWeight(.heavy)
      .font(.system(size:24.0))
      .lineSpacing(15)
      .foregroundColor(.white)
      .frame(width: 300, height: 150, alignment: .center)
      .background(Color.cyan)
      .cornerRadius(15)
      .opacity(0.9)
      , alignment: .bottom )
    .overlay(
      Image(systemName: "play.circle")
      .font(.system(size:100))
      .foregroundColor(.white)
      .opacity(0.9)
      .frame(width:100, height:100, alignment: .bottom))
  }
}

```
<img src="https://raw.githubusercontent.com/ncudemo/yzu-swiftui-1101406/main/IMG_0038.jpeg">
