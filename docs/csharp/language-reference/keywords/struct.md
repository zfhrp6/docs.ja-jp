---
title: "struct (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "struct_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "struct キーワード [C#]"
  - "構造体 [C#], struct キーワード"
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# struct (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`struct` 型は、通常、関連する変数 \(四角形の座標やインベントリ内の項目の特性など\) の小さなグループをカプセル化するのに使用される値型です。  次の例に単純な構造体の宣言を示します。  
  
```  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## 解説  
 構造体には、[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)、[定数](../../../csharp/programming-guide/classes-and-structs/constants.md)、[フィールド](../../../csharp/programming-guide/classes-and-structs/fields.md)、[メソッド](../../../fsharp/language-reference/members/methods.md)、[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)、[インデクサー](../../../csharp/programming-guide/indexers/index.md)、[演算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)、[イベント](../../../csharp/programming-guide/events/index.md)、および[入れ子にされた型](../../../csharp/programming-guide/classes-and-structs/nested-types.md)を含めることができます。ただし、複数のメンバーが必要な場合は、代わりに型をクラスに変更することを検討してください。  
  
 例については、「[構造体の使用](../../../csharp/programming-guide/classes-and-structs/using-structs.md)」を参照してください。  
  
 構造体はインターフェイスを実装できますが、別の構造体から継承することはできません。  そのため、構造体メンバーを `protected` として宣言することはできません。  
  
 詳細については、「[構造体](../../../csharp/programming-guide/classes-and-structs/structs.md)」を参照してください。  
  
## 例  
 使用例を含む詳細については、「[構造体の使用](../../../csharp/programming-guide/classes-and-structs/using-structs.md)」を参照してください。  
  
## C\# 言語仕様  
 例については、「[構造体の使用](../../../csharp/programming-guide/classes-and-structs/using-structs.md)」を参照してください。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [型](../../../csharp/language-reference/keywords/types.md)   
 [値型](../../../csharp/language-reference/keywords/value-types.md)   
 [クラス](../../../csharp/language-reference/keywords/class.md)   
 [interface](../../../csharp/language-reference/keywords/interface.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)