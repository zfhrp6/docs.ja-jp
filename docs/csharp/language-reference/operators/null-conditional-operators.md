---
title: "Null 条件演算子 (C# および Visual Basic) | Microsoft Docs"
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
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Null 条件演算子 (C# および Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

メンバー アクセス \(`?.`\) またはインデックス \(`?[`\) 操作を実行する前に、null をテストするために使用されます。  これらの演算子を使用すると、null チェックの処理のために記述するコードを少なくすることができます \(特に、データ構造を下っていく場合\)。  
  
```c#  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
  
```  
  
```vb  
Dim length = customers?.Length  ‘’ null if customers is null  
Dim first as Customer = customers?(0);  ‘’ null if customers is null  
Dim count as Integer? = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
  
```  
  
 最後の例は、null 条件演算子がショート サーキットであることを示します。  条件付きのメンバー アクセスおよびインデックス操作のチェーンの 1 つの演算が null を返す場合、チェーンの実行の残りの部分は停止します。  式内の優先度の低い他の演算は続行されます。  たとえば、次の式内の `E` は常に実行され、`??` 演算と `==` 演算が実行されます。  
  
```vb-c#  
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
  
```  
  
 null 条件メンバー アクセスの別の用途は、はるかに少ないコードのスレッド セーフな方法でデリゲートを呼び出すことです。  従来の方法には、次のようなコードが必要です。  
  
```c#  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…)  
  
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
  
```  
  
 新しい方法は格段に単純です。  
  
```vb-c#  
PropertyChanged?.Invoke(e)  
  
```  
  
 コンパイラが `PropertyChanged` を評価するためのコードを一度しか生成せず、一時変数に結果が保持されるため、新しい方法はスレッド セーフです。  
  
 null 条件デリゲート呼び出し構文 `PropertyChanged?(e)` がないため、`Invoke` メソッドを明示的に呼び出す必要があります。  それを許可するためのあいまいな解析状況が多すぎました。  
  
## 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
 詳細については、「[Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)」を参照してください。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)   
 [Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md)