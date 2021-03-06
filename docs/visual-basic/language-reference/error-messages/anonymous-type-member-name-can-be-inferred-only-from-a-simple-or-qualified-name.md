---
title: 匿名型メンバーの名前は、引数なしの簡易名または修飾名からのみ推論できます
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: f4f62a9ac97c6dbd8d2426f8bfd17afa66c4001a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587470"
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
