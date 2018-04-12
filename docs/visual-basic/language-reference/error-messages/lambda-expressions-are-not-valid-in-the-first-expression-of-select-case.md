---
title: ラムダ式での最初の式では有効ではありません、&#39;です。場合 &#39; を選択します。ステートメント
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e91401d6891d4e38014bb716a337560885cf73a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a>ラムダ式での最初の式では有効ではありません、&#39;です。場合 &#39; を選択します。ステートメント
テスト式でのラムダ式を使用することはできません、`Select Case`ステートメントです。 ラムダ式の定義を返す関数、およびのテスト式、`Select Case`ステートメントは、基本データ型である必要があります。  
  
 次のコードでは、このエラーが発生します。  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **エラー ID:** BC36635  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   コードを調べて、 `If...Then...Else` ステートメントなどの別の条件構造を使用できないかをご確認ください。  
  
-   指定したこの関数を呼び出して、次のコードに示すように。  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>関連項目  
 [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Select...Case ステートメント](../../../visual-basic/language-reference/statements/select-case-statement.md)
