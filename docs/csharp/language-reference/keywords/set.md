---
title: "set (C# リファレンス)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b810280724dcf608859bfa455947a75ce64b7abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="set-c-reference"></a>set (C# リファレンス)
`set` キーワードは、プロパティまたはインデクサーで、プロパティ値またはインデクサーの要素値を割り当てる "*アクセサー*" メソッドを定義します。 使用例を含む詳細については、「[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)」、「[自動実装プロパティ](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)」、および「[インデクサー](../../../csharp/programming-guide/indexers/index.md)」を参照してください。  
  
次の例では、`Seconds` という名前のプロパティの `get` アクセサーと `set` アクセサーを定義しています。 また、`_seconds` という名前のプライベート フィールドを使って、プロパティの値を戻しています。  
 
 [!code-csharp[set#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  

多くの場合、前の例のように、`set` アクセサーは値を返す 1 つのステートメントで構成されます。 C# 7 以降では、式形式のメンバーとして `set` アクセサーを実装できます。 次の例では、`get` アクセサーと `set` アクセサーの両方を、式形式のメンバーとして実装しています。

 [!code-csharp[set#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
    
プロパティの `get` アクセサーと `set` アクセサーがプライベート バッキング フィールドの値の設定と取得以外の操作を実行しない単純な場合では、自動実装プロパティに対する C# コンパイラのサポートを利用できます。 次の例では、自動実装プロパティとして `Hours` を実装しています。 
  
 [!code-csharp[set#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
    
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)
