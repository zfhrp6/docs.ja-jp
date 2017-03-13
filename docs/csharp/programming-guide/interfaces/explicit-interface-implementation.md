---
title: "明示的なインターフェイスの実装 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "明示的なインターフェイス [C#]"
  - "インターフェイス [C#]、明示的な"
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# 明示的なインターフェイスの実装 (C# プログラミング ガイド)
同じシグネチャを持つメンバーがそれぞれ存在する 2 つのインターフェイスを[クラス](../../../csharp/language-reference/keywords/class.md)が実装した場合、そのメンバーをクラスで実装すると、両方のインターフェイスがそのメンバーをそれぞれの実装として使用することになります。  次の例では、`Paint` へのすべての呼び出しは、同じメソッドを呼び出します。  
  
 [!code-cs[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 ただし、2 つの[インターフェイス](../../../csharp/language-reference/keywords/interface.md) メンバーが同一の機能を実行しない場合は、これらのインターフェイスの一方または両方の実装が不適切になる可能性があります。  そこで、インターフェイス メンバーを明示的に実装し、特定のインターフェイス経由でのみ呼び出され、そのインターフェイスに固有のクラス メンバーを作成できます。  このように実装するには、インターフェイスの名前とピリオドを使ってクラス メンバーに名前を付けます。  次に例を示します。  
  
 [!code-cs[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 クラス メンバー `IControl.Paint` は、`IControl` インターフェイス経由でのみ呼び出され、`ISurface.Paint` は `ISurface` 経由でのみ呼び出されます。  これら 2 つのメソッド実装はそれぞれ独立しており、いずれもクラスで直接呼び出すことができません。  次に例を示します。  
  
 [!code-cs[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 明示的な実装は、次のように、プロパティやメソッドなどの同じ名前を持つ別々のメンバーを 2 つのインターフェイスがそれぞれ宣言するケースを解決する場合にも使用されます。  
  
 [!code-cs[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 これら両方のインターフェイスを実装する場合、クラスでは、プロパティ P またはメソッド P の一方または両方に明示的な実装を適用して、コンパイラのエラーを回避する必要があります。  次に例を示します。  
  
 [!code-cs[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [インターフェイス](../../../csharp/programming-guide/interfaces/index.md)   
 [継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)