---
title: "&#39;です。拡張機能 &#39;属性にのみ適用できます (& a) #39 です。モジュール &#39;、&#39;です。Sub &#39;、または &#39;です。関数 &#39;宣言"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords: BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d77933c52484eb934501107d1ddad15f0eca826
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>&#39;です。拡張機能 &#39;属性にのみ適用できます (& a) #39 です。モジュール &#39;、&#39;です。Sub &#39;、または &#39;です。関数 &#39;宣言
Visual Basic でのデータ型を拡張する唯一の方法では、標準的なモジュールの中に拡張メソッドを定義します。 拡張メソッドを指定できます、`Sub`プロシージャまたは`Function`プロシージャです。 すべての拡張メソッドは、拡張属性と共に設定されなければなりません`<Extension()>`から、<xref:System.Runtime.CompilerServices?displayProperty=nameWithType>名前空間。 必要に応じて、拡張メソッドを含むモジュールの場合は、同じ方法でマークされている可能性があります。 拡張属性の他の使用が有効ではありません。  
  
 **エラー ID:** BC36550  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   拡張属性を削除します。  
  
-   それを囲むモジュールで定義されている、メソッドとして、拡張機能を設計し直します。  
  
## <a name="example"></a>例  
 次の例では定義、`Print`のメソッド、`String`データ型。  
  
```  
Imports StringUtility  
Imports System.Runtime.CompilerServices  
Namespace StringUtility  
    <Extension()>   
    Module StringExtensions  
        <Extension()>   
        Public Sub Print (ByVal str As String)  
            Console.WriteLine(str)  
        End Sub  
    End Module  
End Namespace  
```  
  
## <a name="see-also"></a>関連項目  
 [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)
