---
title: "class (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "class_CSharpKeyword"
  - "class"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "class キーワード [C#]"
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# class (C# リファレンス)
クラスは、次の例に示すように、`class` キーワードを使用して宣言します。  
  
```  
  
      class TestClass  
{  
    // Methods, properties, fields, events, delegates   
    // and nested classes go here.  
}  
```  
  
## 解説  
 単一継承のみ、C で使用できます。  つまり、1 つの基本クラスの実装だけを継承できます。  ただし、クラスは複数のインターフェイスを実装できます。  クラスの継承とインターフェイスの実装の例を次の表に示します。  
  
|継承|例|  
|--------|-------|  
|なし|`class ClassA { }`|  
|Single|`class DerivedClass: BaseClass { }`|  
|なし。2 つのインターフェイスを実装。|`class ImplClass: IFace1, IFace2 { }`|  
|1 つ。1 つのインターフェイスを実装。|`class ImplDerivedClass: BaseClass, IFace1 { }`|  
  
 は、名前空間内で直接宣言する他のクラスに入れ子にされていないクラスは、[パブリック](../../../csharp/language-reference/keywords/public.md) または [内部](../../../csharp/language-reference/keywords/internal.md)のいずれかです。  クラスは既定で `internal` です。  
  
 メンバーを、入れ子になったクラスがクラス、[パブリック](../../../csharp/language-reference/keywords/public.md)、`protected internal`、[プロテクト](../../../csharp/language-reference/keywords/protected.md)、[内部](../../../csharp/language-reference/keywords/internal.md)、または [プライベート](../../../csharp/language-reference/keywords/private.md)のいずれかになります。  メンバーは既定で [プライベート](../../../csharp/language-reference/keywords/private.md) です。  
  
 詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
 型パラメーターを持つジェネリック クラスを宣言できます。  詳細については、[&#91;ジェネリック クラス&#93;](../../../csharp/programming-guide/generics/generic-classes.md)を参照してください。  
  
 クラスは、次のメンバーを宣言できます。  
  
-   [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Destructors](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [定数](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [フィールド](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [インデクサー](../../../csharp/programming-guide/indexers/index.md)  
  
-   [演算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [イベント](../../../csharp/programming-guide/events/index.md)  
  
-   [デリゲート](../../../csharp/programming-guide/delegates/index.md)  
  
-   [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [インターフェイス](../../../csharp/programming-guide/interfaces/index.md)  
  
-   [構造体](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
## 使用例  
 ここでは、クラスのフィールド、コンストラクター、メソッドの宣言例を示します。  オブジェクト インスタンスの作成、インスタンス データの出力の例も示します。  この例では、2 つのクラスを宣言します。`Child` クラスには、2 つのプライベート フィールド \(`name` および `age`\) と、2 つのパブリック メソッドがあります。  2 番目のクラスである `StringTest` は、`Main` の格納に使用されます。  
  
 [!code-cs[csrefKeywordsTypes#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/class_1.cs)]  
  
## コメント  
 上記の例で、プライベート フィールド \(`name` および `age`\) にアクセスできるのは、`Child` クラスのパブリック メソッドだけであることに注意してください。  たとえば、次のステートメントを使用して `Main` メソッドから子供の名前を出力できません。  
  
```  
Console.Write(child1.name);   // Error  
```  
  
 `Main` から `Child` のプライベート メンバーへのアクセスは、`Main` がそのクラスのメンバーである場合にのみ可能です。  
  
 アクセス修飾子を指定せずにクラス内で宣言された型はになります `private`ため、キーワードが削除されてもこの例のデータ メンバーは、`private` です。  
  
 また、既定のコンストラクターを使って作成したオブジェクト \(`child3`\) は、既定では、年齢フィールドが 0 に初期化されることに注意してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)