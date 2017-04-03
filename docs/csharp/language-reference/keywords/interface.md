---
title: "インターフェイス (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- interface_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: 29
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 84759153ebfc77ba6d39e1b3c47a00a083f267c0
ms.lasthandoff: 03/13/2017

---
# <a name="interface-c-reference"></a>インターフェイス (C# リファレンス)
インターフェイスには、[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)、[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)、[イベント](../../../csharp/programming-guide/events/index.md)、[インデクサー](../../../csharp/programming-guide/indexers/index.md)のシグネチャのみが含まれています。 インターフェイスを実装するクラスまたは構造体は、インターフェイス定義で指定されているインターフェイスのメンバーを実装する必要があります。 次の例の `ImplementationClass` クラスは、`SampleMethod` を返す、パラメーターのない `void` メソッドを実装する必要があります。  
  
 使用例を含む詳細については、「[インターフェイス](../../../csharp/programming-guide/interfaces/index.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-cs[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 インターフェイスは、名前空間またはクラスのメンバーであり、次のメンバーのシグネチャを含むことができます。  
  
-   [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [プロパティ](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [インデクサー](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [イベント](../../../csharp/language-reference/keywords/event.md)  
  
 インターフェイスは、1 つ以上の基底インターフェイスから継承できます。  
  
 基本型のリストに基底クラスとインターフェイスが含まれる場合は、基底クラスがリストの最初に表示されます。  
  
 インターフェイスを実装するクラスは、そのインターフェイスのメンバーを明示的に実装できます。 明示的に実装されているメンバーには、クラス インスタンスではアクセスできません。インターフェイスのインスタンスを使用した場合にのみアクセスできます。  
  
 明示的なインターフェイスの実装の詳細とコード例については、「[明示的なインターフェイスの実装](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)」を参照してください。  
  
## <a name="example"></a>例  
 ここでは、インターフェイスの実装例を示します。 この例では、インターフェイスにプロパティ宣言が含まれ、クラスに実装が含まれます。 `IPoint` を実装するクラスのインスタンスには、整数プロパティ `x` および `y` が含まれています。  
  
 [!code-cs[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)   
 [インターフェイス](../../../csharp/programming-guide/interfaces/index.md)   
 [プロパティの使用](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [インデクサーの使用](../../../csharp/programming-guide/indexers/using-indexers.md)   
 [class](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [インターフェイス](../../../csharp/programming-guide/interfaces/index.md)
