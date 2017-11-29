---
title: "struct (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e8a848d5543291ef335e72cb7806158827e865dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="struct-c-reference"></a>struct (C# リファレンス)
`struct` 型は、通常、関連する変数 (四角形の座標やインベントリ内の項目の特性など) の小さなグループをカプセル化するのに使用される値型です。 次の例に単純な構造体の宣言を示します。  
  
```  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a>コメント  
 構造体には、[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)、[定数](../../../csharp/programming-guide/classes-and-structs/constants.md)、[フィールド](../../../csharp/programming-guide/classes-and-structs/fields.md)、[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)、[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)、[インデクサー](../../../csharp/programming-guide/indexers/index.md)、[演算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)、[イベント](../../../csharp/programming-guide/events/index.md)、および[入れ子にされた型](../../../csharp/programming-guide/classes-and-structs/nested-types.md)を含めることができます。ただし、複数のメンバーが必要な場合は、代わりに型をクラスに変更することを検討してください。  
  
 例については、「[構造体の使用](../../../csharp/programming-guide/classes-and-structs/using-structs.md)」を参照してください。  
  
 構造体はインターフェイスを実装できますが、別の構造体から継承することはできません。 そのため、構造体メンバーを `protected` として宣言することはできません。  
  
 詳細については、「[構造体](../../../csharp/programming-guide/classes-and-structs/structs.md)」を参照してください。  
  
## <a name="examples"></a>例  
 例と詳細については、「[構造体の使用](../../../csharp/programming-guide/classes-and-structs/using-structs.md)」を参照してください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 例については、「[構造体の使用](../../../csharp/programming-guide/classes-and-structs/using-structs.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)  
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [型](../../../csharp/language-reference/keywords/types.md)  
 [値型](../../../csharp/language-reference/keywords/value-types.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [interface](../../../csharp/language-reference/keywords/interface.md)  
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)
