
- 10-20(λͺ©-SwiftUI)
    
    ## πΈTeam10 MiracleRandomNum (Up & Down Game)
    
<img width="442" alt="Untitled (8)" src="https://user-images.githubusercontent.com/67450169/196968529-17b42cb6-40e6-44c4-9960-accafad9bce6.png">
<img width="450" alt="Untitled (9)" src="https://user-images.githubusercontent.com/67450169/196968539-29fd3198-3228-4fa5-a7a3-db2ea616eeb6.png">

    ```swift
    //
    //  ContentView.swift
    //  MiracleRandom
    //
    //  Created by Martin on 2022/10/20.
    //
    
    import SwiftUI
    
    //userNumber == "" ? "" : array[arrayIndex]
    //randomNumber == 0 ? "λλ€ μ«μλ₯Ό λ¨Όμ  λ§λ€μ΄μ£ΌμΈμ" : "λλ€ μ«μκ° λ§λ€μ΄μ‘μ΅λλ€"
    
    //1. λλ€λλ²λ₯Ό κ°μ Έμ€λ λ²νΌμ λλ₯Έλ€.
    // λλ€λλ²κ° 0μΌλ‘ λμ΄μμΌλ©΄ νμ€νΈ νλλ μ μΆλ²νΌ λΉνμ±ν
    
    //2. μ μ κ° λ²νΈλ₯Ό μλ ₯νλ€.
    // μ μ κ° μλ¬΄κ²λ μλ ₯μ νμ§ μμλ
    // userNumber.isEmptyλ‘ νμ
    
    //3. μ μ κ° λ²νΌμ λλ¬μ μ λ΅μ νμΈ
    //4. μ λ΅μ΄ λμ¬λκΉμ§ 2 -3 λ°λ³΅
    //5. μ λ΅μ λ§μΆλ©΄ μΆν -> μ΄κΈ°ν
    struct ContentView: View {
        //λλ€μ«μ μ€νμ΄νΈ
        
        let labelTexts: [String] = ["μ λ΅", "μ λ΅λ³΄λ€ μμ μ«μμλλ€.", "μ λ΅λ³΄λ€ ν° μ«μμλλ€.", "μλ ₯ κ°μ΄ μλͺ»λμμ΅λλ€", ""]
        
        
        @State private var labelIndex: Int = 4
        @State private var randomNumber: Int = 0
        @State private var userNumber: String = ""
        @State private var count: Int = 0
        
        var body: some View {
            VStack {
                
                if labelIndex == 0 {
                    AsyncImage(url: URL(string:   "https://media.discordapp.net/attachments/1019072261854081044/1032522053317820477/unknown.png")) { image in
                        image.resizable()
                    } placeholder: {
                        ProgressView()
                    }
                    .frame(width: 300, height: 300)
                }
                
    
                
                //λλ€ μ«μ μμ±νλ λ²νΌ
                randomNumber == 0 ?
                Button("Random") {
                    randomNumber = Int.random(in: 1...100)
                    print(randomNumber)
                }
                .buttonStyle(.bordered)
                .foregroundColor(.orange)
                
                :
                Button("Retry") {
                    randomNumber = 0
                    count = 0
                    userNumber = ""
                    labelIndex = 4
                }
                .buttonStyle(.bordered)
                .foregroundColor(.orange)
                
            
                
                //MARK: μ λ³΄
                //μ λ΅μΈμ§ μ€λ΅μΈμ§
                Text(labelTexts[labelIndex])
                //μλνμ
                Text("μλνμ: \(count)")
                
                //MARK: μλ ₯ νμ€νΈνλ
                TextField("1λΆν° 100μ¬μ΄μ μ«μλ₯Ό μλ ₯νμΈμ", text: $userNumber)
                    .multilineTextAlignment(.center)
                
                //MARK: μ μΆλ²νΌ
                Button("Submit") {
                    // μ¬μ©μκ° μλ ₯ν κ°μ Intλ‘ λ°κΏμ λΉκ΅
                    guard let userNumber = Int(userNumber) else {
                        labelIndex = 3
                        return
                    }
                    
                    
                    
                    switch userNumber {
                    case randomNumber:
                        labelIndex = 0
                        print("μΌμΉ")
                        count += 1
                    case 1 ..< randomNumber :
                        labelIndex = 1
                        print("μμ")
                        count += 1
                    case (randomNumber + 1)...100:
                        labelIndex = 2
                        print("νΌ")
                        count += 1
                    case ...0, 100...:
                        labelIndex = 3
                        print("λ²μλ°")
                    default :
                        print("λν΄νΈ")
                    }
                    
                    
                  
                }
                .buttonStyle(.bordered)
                .foregroundColor(.orange)
                .disabled(randomNumber == 0 )
                .disabled(userNumber.isEmpty)
                
                
                
            }
            .padding()
        }
    }
    
    struct ContentView_Previews: PreviewProvider {
        static var previews: some View {
            ContentView()
        }
    }
    
    //1. νΉμ ν μ«μ κ·μΉμ λ§λ λ€ (μλ₯Ό λ€μ΄ 1~99μ¬μ΄μ μ μ)
    //2. λλ€μ«μλ₯Ό λ§λ€κ³  λ³΄μ¬μ£Όμ§ μλλ€
    //3. μ¬μ©μλ νμ€νΈ μλ ₯μ΄λ νλ©΄μ λ²νΌμ λλ₯΄λ λ±μ λ€μν λ°©λ²μΌλ‘ μ«μλ₯Ό μλ ₯νλ€
    //4. λλ€ μ«μλ₯Ό λ§μΆλ©΄ νλ €νκ³  μλ¦λ€μ΄ μΆν λ©μμ§λ₯Ό λ³΄μ¬μ£Όκ³  λ€μνμ μ§ννλ€
    //5. μ«μλ₯Ό λ§μΆμ§ λͺ»νλ©΄ "λ ν° μ«μ" λλ "λ μ μ μ«μ"μΈ μν©μ μλ €μ€λ€ (μ΅μ)
    ```
