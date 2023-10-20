<h1>HW3</h1>

```swift

import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            TitleView()
            HStack{
                CharactersView(imageName: "Mario")
                CharactersView(imageName: "Luigi")
                CharactersView(imageName: "Peach")
            }
            HStack{
                CharactersView2(imageName: "Yoshi")
                CharactersView2(imageName: "Toad")
                CharactersView2(imageName: "DonkeyKong")
            }
            HStack{
                CharactersView(imageName: "Wario")
                CharactersView(imageName: "Waluigi")
                CharactersView(imageName: "Koopa")
            }
        }
    }
}

struct TitleView: View{
    var body: some View{
        VStack(alignment: .center, spacing: 2){
            Text("Edward")
                .font(.system(size:40))
                .foregroundColor(.yellow)
                .frame(width: 200, height: 70, alignment: .center)
                .background(Color.black)
                .cornerRadius(20)
            Text("Mario Characters Collections")
                .font(.system(size:25))
                .foregroundColor(.yellow)
                .frame(width: 350, height: 50, alignment: .center)
                .background(Color.black)
                .cornerRadius(20)
        }
    }
}

struct CharactersView: View{
    var imageName:String
    var body: some View{
        VStack{
            Image(imageName)
                .resizable()
                .aspectRatio(contentMode:.fit)
                .frame(width: 100, height: 100, alignment: .center)
            Text(imageName.capitalized)
                .fontWeight(.bold)
                .font(.system(size:25))
        }.padding(.all, 2)
    }
}

struct CharactersView2: View{
    var imageName:String
    var body: some View{
        ZStack{
            VStack{
                Image(imageName)
                    .resizable()
                    .aspectRatio(contentMode:.fit)
                    .frame(width: 100, height: 100, alignment: .center)
                Text(imageName.capitalized)
                    .fontWeight(.bold)
                    .font(.system(size:25))
            }.padding(.all, 2)
            Text("SOLD")
                .font(.system(size: 20))
                .foregroundColor(.white)
                .padding(.all, 5)
                .background(Color.red)
                .frame(width: 100, height: 100, alignment: .center)
                .opacity(0.8)
                .offset(x: 35, y: 10)
        }
    }
}

```

<img src="https://raw.githubusercontent.com/ctwoc111/yzu-swiftui-1101406/main/IMG_0064.jpeg">
