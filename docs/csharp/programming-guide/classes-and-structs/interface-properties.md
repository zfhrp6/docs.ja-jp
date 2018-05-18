---
title: インターフェイスのプロパティ (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: bfa03c7ebe82f3f6a03666d908a5fa9d4e386172
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="interface-properties-c-programming-guide"></a>インターフェイスのプロパティ (C# プログラミング ガイド)
[interface](../../../csharp/language-reference/keywords/interface.md) でプロパティを宣言することができます。 インターフェイスのインデクサー アクセサーの例を次に示します。  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 インターフェイス プロパティのアクセサーには、本文はありません。 したがって、アクセサーの目的は、プロパティが読み取り/書き込み、読み取り専用、または書き込み専用のどれかを示すことです。  
  
## <a name="example"></a>例  
 この例では、インターフェイス `IEmployee` に読み取り/書き込み専用のプロパティ `Name` および読み取り専用のプロパティ `Counter` があります。 クラス `Employee` は `IEmployee` インターフェイスを実装し、これら 2 つのプロパティを使用します。 プログラムは、新しい従業員の名前と現在の従業員の数を読み込んで、従業員の名前と計算した従業員番号を表示します。  
  
 メンバーが宣言されているインターフェイスを参照するプロパティの完全修飾名を使用することができます。 例:  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 これは、[明示的なインターフェイスの実装](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)で呼び出されます。 たとえば、`Employee` クラスが 2 つのインターフェイス `ICitizen` と `IEmployee` を実装し、両方のインターフェイスが同じ `Name` プロパティを持っている場合、明示的なインターフェイス メンバーの実装が必要です。 つまり、次のプロパティの宣言があります。  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 これは、`IEmployee` インターフェイスで `Name` プロパティを実装します。次の宣言があります。  
  
 [!code-csharp[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 これは、`ICitizen` インターフェイスで `Name` プロパティを実装します。  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a>出力例  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [プロパティの使用](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [プロパティとインデクサーの比較](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
 [インデクサー](../../../csharp/programming-guide/indexers/index.md)  
 [インターフェイス](../../../csharp/programming-guide/interfaces/index.md)
