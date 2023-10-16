<h1>HW2</h1>

```swift
import SwiftUI

struct ContentView: View 
{
    @State var randomNum:Int = 0
    @State var colorNum:Int = 0
    var body: some View 
    {
        VStack
        {
            let hands = ["👊", "✌️", "🖐️", "👊🏻", "✌🏻", "🖐🏻", 
            "👊🏿", "✌🏿", "🖐🏿"]
            switch (randomNum % 3)
            {
                case 0:
                    Text(hands[randomNum])
                    .padding(.all, 10)
                    .font(.system(size:150))
                    .frame(width: 200, height: 200, alignment: .center)
                    .background(Color.cyan)
                    .clipShape(Circle(), style: FillStyle())
                case 1:
                    Text(hands[randomNum])
                        .padding(.all, 10)
                        .font(.system(size:150))
                        .frame(width: 200, height: 200, alignment: .center)
                        .background(Color.cyan)
                        .clipShape(Circle(), style: FillStyle())
                case 2:
                    Text(hands[randomNum])
                        .padding(.all, 10)
                        .font(.system(size:150))
                        .frame(width: 200, height: 200, alignment: .center)
                        .background(Color.cyan)
                        .clipShape(Circle(), style: FillStyle())
                default:
                    Text("Error")
            }
            
            Button(action: {randomNum = Int.random(in: 0..<3)
                randomNum += colorNum        
            }, label: {
                Text("Press")
                    .padding(.all, 20)
                    .frame(width: 300, height: 100, alignment: .center)
                    .background(Color.pink)
                    .font(.system(size:50))
                    .foregroundColor(.white)
                    .cornerRadius(30)
            })
            
            Button(action: {randomNum += 3
                randomNum %= 9
                colorNum += 3
                colorNum %= 9
            }, label: {
                Text("Change Color")
                    .padding(.all, 20)
                    .frame(width: 300, height: 200, alignment: .center)
                    .background(Color.pink)
                    .font(.system(size:50))
                    .foregroundColor(.white)
                    .cornerRadius(30)
            })
        }
    }
}

```

<img src="https://raw.githubusercontent.com/ctwoc111/yzu-swiftui-1101406/main/IMG_0051.gif">
