---
title: "nameof (C# および Visual Basic リファレンス) | Microsoft Docs"
ms.date: 2017-03-03
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- nameof_CSharpKeyword
- nameof
dev_langs:
- CSharp
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: da3fef282ac71de07057131069bf58d4f761ad2d
ms.contentlocale: ja-jp
ms.lasthandoff: 05/15/2017

---
# <a name="nameof-c-and-visual-basic-reference"></a>nameof (C# および Visual Basic リファレンス)

変数、型、またはメンバーの単純な (修飾されていない) 文字列名を取得するのに使用します。  

コード内のエラーの報告、モデル ビュー コントローラー (MVC) リンクのフック、プロパティの変更されたイベントの起動などの際には、多くの場合、メソッドの文字列名をキャプチャします。  `nameof` の使用は、定義の名前を変更するときに、コードを有効な状態に保つのに役立ちます。  以前は、定義を参照するのに文字列リテラルを使用する必要がありました。ツールには、これらの文字列リテラルを検査する方法がわからないため、コード要素の名前変更の際には当てになりません。  
  
 `nameof` 式のフォームは次のとおりです。  
  
```csharp  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"  
```  
  
## <a name="key-use-cases"></a>主なユース ケース  
 ここでは、`nameof` の主なユース ケースを示します。  
  
 パラメーターの確認:  
 ```csharp  
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
 ```csharp  
int p {  
    get { return this.p; }  
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too  
}  
```  
  
 XAML 依存関係プロパティ:  
 ```csharp  
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));  
```  
  
 ログ:  
 ```csharp  
void f(int i) {  
    Log(nameof(f), "method entry");  
}  
```  
  
 属性:  
 ```csharp  
[DebuggerDisplay("={" + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```  
  
## <a name="examples"></a>使用例  
 ここでは、C# の例をいくつか示します。  
  
```csharp  
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
nameof(f) -> "f"  
nameof(f<T>) -> syntax error  
nameof(f<>) -> syntax error  
nameof(Method2()) -> error "This expression does not have a name"  
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
  
## <a name="remarks"></a>コメント  
 `nameof` への引数は、簡易名、修飾名、メンバー アクセス、メンバーを指定した base アクセス、またはメンバーを指定した this アクセスでなければなりません。  引数の式はコード定義を識別しますが、評価されることはありません。  
  
 引数は構文上、式でなければならないため、許容されないものが多数あります。特に必要がないため、ここではこのようなものについて逐一取り上げていません。  定義済みの型 (たとえば、`int` または `void`)、Null 許容型 (`Point?`)、配列型 (`Customer[,]`)、ポインター型 (`Buffer*`)、修飾されたエイリアス (`A::B`)、バインドされていないジェネリック型 (`Dictionary<,>`)、プリプロセッサ シンボル (`DEBUG`)、およびラベル (`loop:`) はエラーが発生するため、注意が必要です。  
  
 完全修飾名を取得する必要がある場合は、`nameof` と共に `typeof` 式を使用できます。  例:
```csharp  
class C {
    void f(int i) {  
        Log($"{typeof(C)}.{nameof(f)}", "method entry");  
    }
}
``` 

 残念ながら、`typeof` は `nameof` のような定数式ではないので、`nameof` が使われるすべての場所で `nameof` と組み合わせて `typeof` を使うことはできません。  たとえば、次のコードでは CS0182 コンパイル エラーが発生します。
 ```csharp  
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```    
 上記の例では、型名を使用でき、インスタンス メソッド名にアクセスできることが分かります。  評価された式で必要とされるような、型のインスタンスは必要ありません。  型名の使用は状況によっては非常に便利です。型名では名前を参照しているだけでインスタンス データを使用してはいないため、インスタンス変数や式を考慮する必要はありません。  
  
 クラスの属性式内でクラスのメンバーを参照できます。  
  
 "`Method1 (str, str)`" などの署名情報を取得する方法はありません。  そうする 1 つの方法は、`Expression e = () => A.B.Method1("s1", "s2")` という式を使用し、結果として得られる式ツリーから MemberInfo を取得することです。  
  
## <a name="language-specifications"></a>言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 詳しくは、「[Visual Basic 言語リファレンス](../../../visual-basic/language-reference/index.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [Visual Basic 言語リファレンス](../../../visual-basic/language-reference/index.md)   
 [Visual Basic プログラミング ガイド](../../../visual-basic/programming-guide/index.md)

