---
title: "static (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "static"
  - "static_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "static キーワード [C#]"
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# static (C# リファレンス)
`static` 修飾子は、静的メンバーの宣言に使用します。静的メンバーは、特定のオブジェクトではなく、型自体に属するメンバーです。  `static` 修飾子は、クラス、フィールド、メソッド、プロパティ、演算子、イベント、およびコンストラクターと組み合わせて使用できますが、インデクサー、デストラクター、またはクラス以外の型で使用することはできません。  詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  
  
## 使用例  
 次のクラスは `static` として宣言され、`static` メソッドのみが含まれます。  
  
 [!code-cs[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 定数宣言や型宣言は、暗黙に静的メンバーです。  
  
 静的メンバーは、インスタンスを使って参照できません。  代わりに、型の名前を使って参照します。  たとえば、次のクラスを考えます。  
  
 [!code-cs[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 静的メンバー `x` を参照するには、同じスコープからその静的メンバーにアクセス可能でない限り、完全修飾名 \(`MyBaseC.MyStruct.x`\) を使用します。  
  
```c#  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 クラスのインスタンスには同クラスのすべてのインスタンス フィールドのコピーが別に含まれますが、各静的フィールドのコピーは 1 つだけです。  
  
 静的メソッドまたは静的プロパティ アクセサーへの参照には、[this](../../../csharp/language-reference/keywords/this.md) は使用できません。  
  
 `static` キーワードをクラスに適用する場合、そのクラスのすべてのメンバーが静的であることが必要です。  
  
 クラスおよび静的クラスには、静的コンストラクターを含めることができます。  静的コンストラクターは、プログラム開始時点からクラスがインスタンス化される時点までの間に呼び出されます。  
  
> [!NOTE]
>  `static` キーワードの用法は、C\+\+ の場合よりも制限されています。  C\+\+ キーワードと比較するには、「[スタティック](/visual-cpp/misc/static-cpp)」を参照してください。  
  
 静的メンバーを例示するために、ある企業の従業員を表すクラスを考えてみます。  このクラスには、従業員の数を数えるメソッドと、従業員の数を格納するフィールドがあると仮定します。  メソッドおよびフィールドは共に、従業員のどのインスタンスにも属していません。  代わりに、それらは企業のクラスに属しています。  このため、クラスの静的なメンバーとして宣言する必要があります。  
  
## 使用例  
 この例では、新しい従業員の名前と ID を読み取り、従業員数のカウンターを 1 インクリメントして、新しい従業員の情報および新しい従業員総数を表示します。  簡略化のために、この例では現在の従業員数をキーボード入力から読み取っています。  実際のアプリケーションでは、ファイルから情報を読み取るようにしてください。  
  
 [!code-cs[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## 使用例  
 この例では、宣言されていない別の静的フィールドを使用して静的フィールドを初期化することはできても、静的フィールドに値を明示的に割り当てない限り、結果は未定義になることを示します。  
  
 [!code-cs[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)