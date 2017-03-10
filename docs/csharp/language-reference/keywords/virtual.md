---
title: "virtual (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "virtual_CSharpKeyword"
  - "virtual"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "virtual キーワード [C#]"
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# virtual (C# リファレンス)
`virtual` キーワードは、メソッド、プロパティ、インデクサー、またはイベントの宣言を修飾し、派生クラスでオーバーライドできるようにするために使用します。  たとえば、このメソッドは、このメソッドを継承するクラスでオーバーライドできます。  
  
```  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 仮想メンバーの実装は、[オーバーライドするメンバー](../../../csharp/language-reference/keywords/override.md)によって派生クラスで変更できます。  `virtual` キーワードを使用する方法の詳細については、「[Override キーワードと New キーワードによるバージョン管理](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)」および「[Override キーワードと New キーワードを使用する場合について](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)」を参照してください。  
  
## 解説  
 仮想メンバーが呼び出されるときには、オブジェクトの実行時の型が、オーバーライドするメンバーで確認されます。  メンバーをオーバーライドしている派生クラスがない場合には、おそらくはオリジナルのメンバーである、最派生クラスでオーバーライドするメンバーが呼び出されます。  
  
 既定では、これらのメソッドは非仮想です。  非仮想メソッドのオーバーライドはできません。  
  
 `virtual` 修飾子は、`static`、`abstract, private`、または `override` の各修飾子と一緒には使用できません。  仮想プロパティの例を次に示します。  
  
 [!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#26)]  
  
 仮想プロパティは抽象メソッドと同様に動作しますが、宣言の構文および呼び出しの構文に相違があります。  
  
-   静的プロパティで `virtual` 修飾子を使用するのはエラーです。  
  
-   継承された仮想プロパティを派生クラス内でオーバーライドできます。オーバーライドするには、`override` 修飾子を使用しているプロパティ宣言をインクルードします。  
  
## 使用例  
 この例では`Shape` のクラスに 2 本の座標 `x``y` と `Area()` の仮想メソッドがあります。  図形のクラス、たとえば `Circle`、`Cylinder`、および `Sphere` が `Shape` クラスを継承し、各図形について、表面積が計算されます。  各派生クラスには、`Area()` の独自のオーバーライド実装があります。  
  
 次の宣言に示すように継承クラス `Circle``Sphere` と `Cylinder` 基本クラスを初期化するすべてのコンストラクターを使用してください。  
  
```  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 次のプログラムはメソッドに関連付けられたオブジェクトへ `Area()` ためのメソッドの適切な実装を呼び出すことによって各図形の適切な領域を計算して表示します。  
  
 [!code-cs[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefKeywordsModifiers/csrefKeywordsModifiers.cs#23)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [ポリモーフィズム](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)   
 [abstract](../../../csharp/language-reference/keywords/abstract.md)   
 [オーバーライド](../../../csharp/language-reference/keywords/override.md)   
 [new](../../../csharp/language-reference/keywords/new.md)