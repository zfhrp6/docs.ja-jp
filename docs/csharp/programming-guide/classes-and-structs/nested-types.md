---
title: "入れ子にされた型 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "入れ子にされた型 [C#]"
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# 入れ子にされた型 (C# プログラミング ガイド)
[クラス](../../../csharp/language-reference/keywords/class.md)や[構造体](../../../csharp/language-reference/keywords/struct.md)の中で定義された型は、入れ子にされた型と呼ばれます。  たとえば、次のようになります。  
  
 [!code-cs[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/nested-types_1.cs)]  
  
 外側の型がクラスまたは構造体のいずれであっても、入れ子にされた型は既定で [private](../../../csharp/language-reference/keywords/private.md) になりますが、[public](../../../csharp/language-reference/keywords/public.md)、protected internal、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、または [private](../../../csharp/language-reference/keywords/private.md) にすることもできます。  上の例の `Nested` は、外部の型からアクセスできませんが、次のように public にもできます。  
  
 [!code-cs[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/nested-types_2.cs)]  
  
 入れ子にされた型 \(内側の型\) は、包含する型 \(外側の型\) にアクセスできます。  包含する型にアクセスするには、その型を入れ子にされた型にコンストラクターとして渡します。  たとえば、次のようになります。  
  
 [!code-cs[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/nested-types_3.cs)]  
  
 入れ子にされた型は、包含する型にアクセス可能なすべてのメンバーにアクセスできます。  入れ子にされた型は、継承されたプロテクト メンバーを含む、包含する型のプライベート メンバーとプロテクト メンバーにアクセスできます。  
  
 上記の宣言では、クラス `Nested` の完全名は `Container.Nested` です。  これは、次のように入れ子になったクラスの新しいインスタンスを作成するときに使用される名前です。  
  
 [!code-cs[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/nested-types_4.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)