---
title: "nameof (C# および Visual Basic リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# nameof (C# および Visual Basic リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

変数、型、またはメンバーの単純な \(修飾されていない\) 文字列名を取得するのに使用されます。  コード内のエラーの報告、モデル ビュー コントローラー \(MVC\) リンクのフック、プロパティの変更されたイベントの起動などの際には、多くの場合、メソッドの文字列名をキャプチャします。  `nameof` の使用は、定義の名前を変更するときに、コードを有効な状態に保つのに役立ちます。  以前は、定義を参照するのに文字列リテラルを使用する必要がありました。ツールには、これらの文字列リテラルを検査する方法が分からないため、コード要素の名前変更の際には当てになりません。  
  
 `nameof` 式のフォームは次のとおりです。  
  
```c#  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode”  
  
```  
  
## キー ユース ケース  
 これらの例は、`nameof` のキー ユース ケースを示します。  
  
 パラメーターの確認:  
 ```c#  
void f(string s) {  
    if (s == null) throw new ArgumentNullException(nameof(s));  
}  
  
```  
  
 MVC アクション リンク:  
 ```html  
<%= Html.ActionLink("Sign up",  
             @typeof(UserController),  
             @nameof(UserController.SignUp))  
%>  
  
```  
  
 INotifyPropertyChanged:  
 ```c#  
int p {  
    get { return this.p; }  
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too  
}  
  
```  
  
 XAML 依存関係プロパティ:  
 ```c#  
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));  
  
```  
  
 ログ:  
 ```c#  
void f(int i) {  
    Log(nameof(f), "method entry");  
}  
  
```  
  
 属性:  
 ```c#  
[DebuggerDisplay("={" + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```  
  
## 使用例  
 C\# のいくつかの例:  
  
```c#  
using Stuff = Some.Cool.Functionality  
class C {  
    static int Method1 (string x, int y) {}  
    static int Method1 (string x, string y) {}  
    int Method2 (int z) {}  
    string f<T>() => nameof(T);  
}  
  
var c = new C()  
  
nameof(C) -> "C"  
nameof(C.Method1) -> "Method1"   
nameof(C.Method2) -> "Method2"  
nameof(c.Method1) -> "Method1"   
nameof(c.Method2) -> "Method2"  
nameof(z) -> "z" // inside of Method2 ok, inside Method1 is a compiler error  
nameof(Stuff) = "Stuff"  
nameof(T) -> "T" // works inside of method but not in attributes on the method  
nameof(f) -> “f”  
nameof(f<T>) -> syntax error  
nameof(f<>) -> syntax error  
nameof(Method2()) -> error “This expression does not have a name”  
  
```  
  
 上記のサンプルの多くは、Visual Basic に適用されます。  特定の Visual Basic の例をいくつか示します。  
  
```vb  
NameOf(a!Foo) -> ' error  "This expression does not have a name"  
NameOf(dict("Foo")) -> ' error  "This expression does not have a name": default property access  
NameOf(dict.Item("Foo")) -> ' error  "This expression does not have a name"  
NameOf(arr(2)) -> ' error  "This expression does not have a name": array element index  
Dim x = Nothing   
NameOf(x.ToString(2)) -> ' error  "This expression does not have a name"  
Dim o = Nothing  
NameOf(o.Equals) -> ' result "Equals".  Warning: "Access of static member of instance; instance will not be evaluated"  
  
```  
  
## コメント  
 `nameof` への引数は、簡易名、修飾名、メンバー アクセス、指定したメンバーを含むベース アクセス、または指定したメンバーを含むこのアクセスでなければなりません。  引数の式はコード定義を識別しますが、評価されることはありません。  
  
 引数は構文上、式でなければならないため、一覧には不要な、許可されていないものが多くあります。  定義済みの型 \(たとえば、`int` または `void`\)、Null 許容型 \(`Point?`\)、配列型 \(`Customer[,]`\)、ポインター型 \(`Buffer*`\)、修飾されたエイリアス \(`A::B`\)、バインドされていないジェネリック型 \(`Dictionary<,>`\)、プリプロセッサ シンボル \(`DEBUG`\)、およびラベル \(`loop:`\) は、エラーを発生させる原因として注意すべきです。  
  
 完全修飾名を取得する必要がある場合は、`nameof` と共に `typeof` 式を使用できます。  
  
 上記の例では、型名を使用でき、インスタンス メソッド名にアクセスできることが分かります。  評価された式で必要とされるような、型のインスタンスは必要ありません。  型名の使用は状況によっては非常に便利な場合があり、名前を参照しているだけでインスタンス データを使用してはいないため、インスタンス変数や式を考案する必要はありません。  
  
 クラスの属性式内でクラスのメンバーを参照できます。  
  
 "`Method1 (str, str)`" などの署名情報を取得する方法はありません。  そうする 1 つの方法は、`Expression e = () => A.B.Method1("s1", "s2")` という式を使用し、結果として得られる式ツリーから MemberInfo を取得することです。  
  
## 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
 詳細については、「[Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)」を参照してください。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)   
 [Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md)