---
title: "方法: 読み取り/書き込みのプロパティの宣言と使用 (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "get アクセサー [C#], プロパティの宣言"
  - "set アクセサー [C#]"
  - "プロパティ [C#], 宣言"
  - "読み取り/書き込みプロパティ [C#]"
  - "アクセサー [C#], 使用してプロパティの宣言"
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法: 読み取り/書き込みのプロパティの宣言と使用 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プロパティは、オブジェクトのデータへの保護されていない、制御されず未確認のアクセスに伴うリスクなしにパブリック データ メンバーの利便性を提供します。  このような機能は、*アクセサー*を通じて実現されます。アクセサーは、基になるデータ メンバーの値を割り当てたり、取得したりする特殊なメソッドです。  [set](../../../csharp/language-reference/keywords/set.md) アクセサーは、データ メンバーの割り当てを可能にし、[get](../../../csharp/language-reference/keywords/get.md) アクセサーは、データ メンバーの値を取得します。  
  
 次の例は、`Name` \(string 型\) と `Age` \(int 型\) の 2 つのプロパティを持つ `Person` クラスを示しています。  次のプロパティは共に `get` アクセサーと `set` アクセサーを備えているので、読み書き可能プロパティと見なされます。  
  
## 使用例  
 [!code-cs[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## 信頼性の高いプログラミング  
 上の例の `Name` プロパティと `Age` プロパティは[パブリック](../../../csharp/language-reference/keywords/public.md)であり、`get` アクセサーと `set` アクセサーの両方を含んでいます。  このため、任意のオブジェクトがこれらのプロパティを読み書きできます。  ただし、これらのアクセサーのうち一方のみの実行が必要になる場合もあります。  たとえば、`set` アクセサーを省略すると、プロパティは読み取り専用になります。この例を次に示します。  
  
 [!code-cs[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 また、一方のアクセサーをパブリックに公開し、もう一方をプライベートまたはプロテクトにすることもできます。  詳細については、「[非対称アクセサーのアクセシビリティ \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)」を参照してください。  
  
 プロパティを宣言すると、プロパティをクラスのフィールドのように使用できます。  このため、プロパティ値の取得と設定の両方で、次のように自然な構文を使用できます。  
  
 [!code-cs[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 プロパティの `set` メソッドでは、特殊な `value` 変数を使用できます。  この変数には、ユーザーが指定した値が含まれます。たとえば、次のように指定します。  
  
 [!code-cs[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 `Person` オブジェクトの `Age` プロパティの値を増加させるには、次のような簡潔な構文を使用できます。  
  
 [!code-cs[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 `set` メソッドと `get` メソッドがそれぞれ使用されてプロパティがモデル化されている場合、上記と同じ内容のコードは次のようになります。  
  
```  
person.SetAge(person.GetAge() + 1);   
```  
  
 この例では、`ToString` メソッドが次のようにオーバーライドされています。  
  
 [!code-cs[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 このプログラムでは、`ToString` メソッドが明示的に使用されていないことに注意してください。  このメソッドは、既定で `WriteLine` 呼び出しによって呼び出されます。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)