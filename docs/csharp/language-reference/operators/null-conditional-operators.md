---
title: "Null 条件演算子 (C# および Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c95b4079cf4e71c0ef9cd436ec230337f512229a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="null-conditional-operators-c-and-visual-basic"></a>Null 条件演算子 (C# および Visual Basic)
メンバー アクセス (`?.`) またはインデックス (`?[`) 操作を実行する前に、null をテストするために使用されます。  これらの演算子を使用すると、null チェックの処理のために記述するコードを少なくすることができます (特に、データ構造を下っていく場合)。  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 最後の例は、null 条件演算子がショート サーキットであることを示します。  条件付きのメンバー アクセスおよびインデックス操作のチェーンの 1 つの演算が null を返す場合、チェーンの実行の残りの部分は停止します。  式内の優先度の低い他の演算は続行されます。  たとえば、次の 2 行目にある `E` が実行され、`??` 演算と `==` 演算が実行されます。  1 行目の `??` はショート サーキットであり、左辺が null 以外に評価されると、`E` は実行されません。
  
```csharp
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
```

```vb
A?.B?.C?(0) ?? E  
A?.B?.C?(0) == E  
```  
  
 null 条件メンバー アクセスの別の用途は、はるかに少ないコードのスレッド セーフな方法でデリゲートを呼び出すことです。  従来の方法には、次のようなコードが必要です。  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 新しい方法は格段に単純です。  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 コンパイラが `PropertyChanged` を評価するためのコードを一度しか生成せず、一時変数に結果が保持されるため、新しい方法はスレッド セーフです。  
  
 null 条件デリゲート呼び出し構文 `PropertyChanged?(e)` がないため、`Invoke` メソッドを明示的に呼び出す必要があります。  それを許可するためのあいまいな解析状況が多すぎました。  
  
## <a name="language-specifications"></a>言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 詳しくは、「[Visual Basic 言語リファレンス](../../../visual-basic/language-reference/index.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [??(null 合体演算子)](null-conditional-operator.md)  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [Visual Basic の言語リファレンス](../../../visual-basic/language-reference/index.md)  
 [Visual Basic プログラミング ガイド](../../../visual-basic/programming-guide/index.md)
