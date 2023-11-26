<h1>HW4</h1>

```swift

import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            HStack{
                Image(systemName: "teddybear.fill")
                    .font(.largeTitle)
                Text("UBear Eats")
                    .font(.largeTitle)
                    .fontWeight(.heavy)
                    .foregroundStyle(.primary)
            }
            TabView{
                Group{
                    WelcomeView()
                        .tabItem { 
                            Image(systemName: "bag")
                            Text("首頁")
                        }
                    ListView()
                        .tabItem { 
                            Image(systemName: "list.bullet.clipboard")
                            Text("類別")
                        }
                    CouponView()
                        .tabItem { 
                            Image(systemName: "ticket")
                            Text("優惠券")
                        }
                }
                .toolbarBackground(Color.black, for: .tabBar)
                .toolbarBackground(.visible, for: .tabBar)
            }
            .tint(.yellow)
        }
    }
}
//--separate line--//
import SwiftUI

struct TermAndDescription: Identifiable{
    var id = UUID()
    var title: String
    var term: String
    var description: String
    var img: String
}

var myDictionary = [
    TermAndDescription(title: "首次註冊 UBear Eats",term: "一個月內免運費", description: "詳細請參閱網站", img: "Bear_Selfie"),
    TermAndDescription(title: "生鮮雜貨月", term: "生鮮雜貨 85 折", description: "詳細請參閱網站", img: "Bear_Cookie"),
    TermAndDescription(title: "生日禮物", term: "當月壽星全品項 50% off 乙次", description: "使用期限當月一個月", img: "Bear_Birthday"),
    TermAndDescription(title: "加入UBear Eats會員", term: "享有各種福利與優惠", description: "優惠詳細請參閱網站", img: "Bear_Love")
]

struct WelcomeView: View {
    @State var currentCard = 0
    var body: some View {
        VStack{
            Image(myDictionary[currentCard].img)
                .resizable()
                .aspectRatio(contentMode: .fit)
            VStack{
                Text(myDictionary[currentCard].title)
                    .font(.largeTitle)
                    .padding(.all, 10)
                Text(myDictionary[currentCard].term)
                    .font(.title)
                    .padding(.all, 10)
                Text(myDictionary[currentCard].description)
                    .font(.title2)
                    .padding(.all, 10)
                    .foregroundColor(.white)
            }
            .frame(width: 350, height: 200, alignment: .center)
            .background(Color.yellow)
            .cornerRadius(20.0)
            .onTapGesture{
                if(currentCard < myDictionary.count - 1){
                    currentCard += 1
                }else{
                    currentCard = 0
                }
            }
            Text("點擊查看下一張")
                .padding(.all, 10)
        }
    }
}
//--separate line--//
import SwiftUI

struct Food: Identifiable{
    var id = UUID()
    var name: String
    var image: String
}

var foods = [
    Food(name: "生鮮雜貨", image: "Fruit"), Food(name: "飲料", image: "Beverage"), Food(name: "食物", image: "Food"), Food(name: "衛生用品", image: "Tissue"), Food(name: "甜點", image: "Dessert")
]

struct BasicImageRow: View{
    var thisFood: Food
    var body: some View{
        HStack{
            Image(thisFood.image)
                .resizable()
                .frame(width: 40, height: 40)
                .cornerRadius(10.0)
            Text(thisFood.name)
        }
    }
}

struct ListView: View{
    var body: some View{
        NavigationView{
            List(foods){ foodItem in
                NavigationLink( destination: FoodDetailView(thisFood: foodItem), label: {
                    BasicImageRow(thisFood: foodItem)
                })
            }
            .navigationBarTitle("購買列表")
        }
    }
}

struct FoodDetailView: View{
    var thisFood: Food
    var body: some View{
        VStack{
            Image(thisFood.image)
                .resizable()
                .aspectRatio(contentMode: .fit)
                .clipped()
            Text(thisFood.name)
                .font(.system(.title, design: .rounded))
                .fontWeight(.black)
            Spacer()
        }
    }
}
//--separate line--//
import SwiftUI

struct Coupon: Identifiable{
    var id = UUID()
    var img: String
    var couponItem: String
    var couponDetail: String
    var couponTime: String
}

var coupons = [
    Coupon(img: "Fish", couponItem: "生鮮雜貨" , couponDetail: "生鮮雜貨 85 折", couponTime: "12 days"), Coupon(img: "ShoppingCar", couponItem: "運費" , couponDetail: "免運", couponTime: "12 days"), Coupon(img: "Cake", couponItem: "特殊優惠" , couponDetail: "5 折優惠券", couponTime: "12 days"), Coupon(img: "ShoppingCar", couponItem: "運費" , couponDetail: "滿 $499 免運", couponTime: "12 days")
]

struct CouponView: View{
    var body: some View{
        VStack{
            Text("我的優惠券")
                .font(.title)
                .padding(.all, 5)
            ScrollView{
                ForEach(coupons){
                    thisCoupon in
                    CardView(img: thisCoupon.img, FoodItem: thisCoupon.couponItem, FoodDetail: thisCoupon.couponDetail, FoodTime: thisCoupon.couponTime)
                }
            }
        }
    }
}
//--separate line--//
import SwiftUI

struct CardView: View{
    var img: String
    var FoodItem: String
    var FoodDetail: String
    var FoodTime: String
    var body:some View{
        VStack {
            Image(img)
                .resizable()
                .aspectRatio(contentMode: .fit)
            VStack(alignment: .leading, content:{
                Text(FoodItem)
                    .font(.headline)
                Text(FoodDetail)
                    .font(.title)
                    .foregroundStyle(.primary)
                    .lineLimit(3)
                Text(FoodTime)
                    .font(.caption)
                    .foregroundStyle(.green)
            })
            .frame(minWidth: 0, idealWidth: 100, maxWidth: .infinity, alignment: .leading)
            .padding(.leading, 20)
            .padding(.bottom, 20)
        }
        .background(Color(red: 255/255, green: 204/255, blue: 153/255))
        .clipShape(.rect(cornerRadius: 20))
        .overlay(RoundedRectangle(cornerRadius : 20)
            .stroke(Color.gray, lineWidth: 2))
        .padding(.all, 10)
    }
}

```

<p><a href = "https://youtu.be/7uDvslZ02vE">hw4 video</a></p>
