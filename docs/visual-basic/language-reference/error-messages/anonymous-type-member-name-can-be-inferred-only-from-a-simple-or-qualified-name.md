---
title: 匿名型メンバーの名前は、引数なしの簡易名または修飾名からのみ推論できます
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7068928a17ee5fdb7bf6b5e0a40aaa7e5ef32f11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>匿名型メンバーの名前は、引数なしの簡易名または修飾名からのみ推論できます
複雑な式からは、匿名型メンバーの名前を推論することはできません。  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 匿名型元となることができます、メンバー名と型を推論できませんソースの詳細については、次を参照してください。[する方法: 匿名型の宣言におけるプロパティ名の推論と型](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)です。  
  
 **エラー ID:** BC36556  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   次のコードに示すように、メンバー名に式を割り当てます。  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a>関連項目  
 [匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
