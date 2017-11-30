---
title: "範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords: BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c986fcf188482c526c53ddf3019cec5163d0b62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>範囲変数の名前は、引数なしの簡易名または修飾名からのみ推論できます
1 つまたは複数の引数を受け取るプログラミング要素は、LINQ クエリに含まれます。 コンパイラは、このプログラミング要素の範囲変数を推論できません。  
  
 **エラー ID:** BC36599  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  次のコードに示すように、プログラミング要素の明示的な変数名を指定します。  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
