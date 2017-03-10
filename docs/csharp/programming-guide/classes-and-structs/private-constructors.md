---
title: "プライベート コンストラクター (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, プライベート コンストラクター"
  - "プライベート コンストラクター [C#]"
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# プライベート コンストラクター (C# プログラミング ガイド)
プライベート コンストラクターは、特別なインスタンス コンストラクターです。  通常は、静的メンバーだけを含むクラスで使用されます。  クラスに 1 つ以上のプライベート コンストラクターがあり、パブリック コンストラクターがない場合、他のクラス \(入れ子になったクラスを除く\) はこのクラスのインスタンスを作成できません。  次に例を示します。  
  
 [!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/private-constructors_1.cs)]  
  
 空のコンストラクターを宣言すると、既定コンストラクターの自動生成は行われません。  コンストラクターにアクセス修飾子を指定しない場合でも、コンストラクターは既定でプライベートになります。  しかし、通常は、[private](../../../csharp/language-reference/keywords/private.md) 修飾子を明示的に使って、クラスをインスタンス化できないことを明確に示します。  
  
 プライベート コンストラクターは、<xref:System.Math> クラスなどのようにインスタンス フィールドやメソッドが存在しない場合や、クラスのインスタンスを取得するためにメソッドが呼び出される場合に、クラスのインスタンスが作成されないようにするために使用します。  クラス内のすべてのメソッドが静的な場合は、クラス全体を静的にすることを検討してください。  詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  
  
## 使用例  
 プライベート コンストラクターを使用するクラスの例を次に示します。  
  
 [!code-cs[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/private-constructors_2.cs)]  
  
 この例で次のステートメントのコメントを解除すると、保護レベルのためにコンストラクターにアクセスできなくなり、エラーが発生します。  
  
 [!code-cs[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/private-constructors_3.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [デストラクター](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [public](../../../csharp/language-reference/keywords/public.md)