---
title: "Expression は値であるため、代入式のターゲットにすることはできません。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords: BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bec3e2d298160bd0b459dc3b7ef93b94648e439a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>Expression は値であるため、代入式のターゲットにすることはできません。
ステートメントでは、式に値を代入しようとしています。 実行時に、書き込み可能な変数、プロパティ、または配列要素にのみ値を割り当てることができます。 次の例では、このエラーが発生する方法を示しています。  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 同様の例は、プロパティと配列の要素に適用でした。  
  
 **間接的なアクセス。** 値型を通じて間接的にアクセスには、このエラーを生成できます。 値を設定しようとしています。 次のコード例を検討してください<xref:System.Drawing.Point>を通じて間接的にアクセスして<xref:System.Windows.Forms.Control.Location%2A>です。  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 割り当てを一時的なのみを作成するために前の例の最後のステートメントが失敗した、<xref:System.Drawing.Point>によって返される構造体、<xref:System.Windows.Forms.Control.Location%2A>プロパティです。 構造体は、値の型と、ステートメントの実行後、一時的な構造は保持されません。 宣言との変数を使用して、問題が解決<xref:System.Windows.Forms.Control.Location%2A>の永続的な割り当てを作成する、<xref:System.Drawing.Point>構造体。 次の例では、前の例の最後のステートメントを置き換えることができるコードを示します。  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 **エラー ID:** BC30068  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ステートメントは、式に値を割り当てます場合、は、1 つの書き込み可能な変数、プロパティ、または配列要素で式を置き換えます。  
  
-   ステートメントが値型 (通常は構造体) を通じて間接的にアクセスする場合、値の型を保持する変数を作成します。  
  
-   適切な構造体 (またはその他の値の型) を変数に代入します。  
  
-   値を代入するのにプロパティにアクセスするのにには、変数を使用します。  
  
## <a name="see-also"></a>関連項目  
 [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)  
 [プロシージャのトラブルシューティング](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
