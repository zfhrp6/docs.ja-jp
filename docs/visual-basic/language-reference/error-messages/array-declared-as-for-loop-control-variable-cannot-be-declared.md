---
title: "ループ コントロール変数として宣言された配列を初期サイズで宣言することはできません"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords: BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0635e1b18b24a241fabad6d67da34f8dde9530db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a>ループ コントロール変数として宣言された配列を初期サイズで宣言することはできません
A`For Each`ループとして配列を使用してその*要素*繰り返し変数がその配列を初期化します。  
  
 次のステートメントでは、このエラーを生成する方法を示しています。  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 最初の`For Each`ステートメントの要素にアクセスするための正しい方法は、`arrayList`です。 2 番目`For Each`ステートメントは、このエラーを生成します。  
  
 **エラー ID:** BC32039  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   宣言から初期化を削除、*要素*繰り返し変数。  
  
## <a name="see-also"></a>関連項目  
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [コレクション](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
