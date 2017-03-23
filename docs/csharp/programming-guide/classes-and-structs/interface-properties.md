---
title: "インターフェイスのプロパティ (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "インターフェイス [C#], プロパティ"
  - "プロパティ [C#], インターフェイス上"
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# インターフェイスのプロパティ (C# プログラミング ガイド)
[interface](../../../csharp/language-reference/keywords/interface.md) に対してプロパティを宣言できます。  次に示すのは、インターフェイス インデクサーのアクセサーの例です。  
  
 [!code-cs[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 インターフェイス プロパティのアクセサーには、本体がありません。  したがって、アクセサーの目的は、プロパティが読み取り\/書き込み、読み取り専用、または書き込み専用のいずれであるかを示すことです。  
  
## 使用例  
 次の例では、インターフェイス `IEmployee` には、読み取り\/書き込みプロパティ `Name` と読み取り専用プロパティ `Counter` があります。  `Employee` クラスは `IEmployee` インターフェイスを実装し、この 2 つのプロパティを使用します。  プログラムは、新しい従業員の名前と現在の従業員数を読み取り、従業員の名前と計算した従業員番号を表示します。  
  
 プロパティの完全修飾名を使用して、メンバーが宣言されているインターフェイスを参照しています。  次に例を示します。  
  
 [!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 これは、「[明示的なインターフェイスの実装](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)」と呼ばれます。  たとえば、`Employee` クラスが 2 つのインターフェイス `ICitizen` と `IEmployee` を実装し、両方のインターフェイスに `Name` プロパティがある場合は、明示的なインターフェイス メンバーの実装が必要になります。  つまり、次のプロパティ宣言では  
  
 [!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 `IEmployee` インターフェイスの `Name` プロパティが実装されます。一方、次の宣言では  
  
 [!code-cs[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 `ICitizen` インターフェイスの `Name` プロパティが実装されます。  
  
 [!code-cs[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## 出力例  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [プロパティの使用](../../../csharp/programming-guide/classes-and-structs/using-properties.md)   
 [プロパティとインデクサーの比較](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)   
 [インデクサー](../../../csharp/programming-guide/indexers/index.md)   
 [インターフェイス](../../../csharp/programming-guide/interfaces/index.md)