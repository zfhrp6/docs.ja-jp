---
title: 変数 &#39;&lt;variablename&gt;&#39; それを囲むブロック内の変数を非表示になります
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2af570cd002b4be4e15a7c03b0ffc2ff84ba3982
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a>変数 &#39;&lt;variablename&gt;&#39; それを囲むブロック内の変数を非表示になります
ブロックで囲まれた変数では、別のローカル変数と同じ名前を持っています。  
  
 **エラー ID:** BC30616  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   囲まれたブロック内の変数の名前を変更して、その他のローカル変数と同じではないようにします。 例:  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   このエラーの一般的な原因は、使用する`Catch e As Exception`イベント ハンドラー。 大文字と小文字の場合は、名前、`Catch`ブロック変数`ex`なく`e`です。  
  
-   このエラーのもう 1 つの一般的な原因は内で宣言されたローカル変数へのアクセスに、`Try`別個のブロック`Catch`ブロックします。 これを修正するには、外部変数を宣言、`Try...Catch...Finally`構造体。  
  
## <a name="see-also"></a>関連項目  
 [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [変数宣言](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
