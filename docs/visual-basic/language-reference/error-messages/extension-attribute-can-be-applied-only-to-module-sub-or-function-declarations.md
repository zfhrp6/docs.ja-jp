---
title: '&#39;拡張機能&#39;属性にのみ適用できます&#39;モジュール&#39;、 &#39;Sub&#39;、または&#39;関数&#39;宣言'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: d7f8829cb879d612711ac6bcc6bf4aa065fbe323
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587320"
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>&#39;拡張機能&#39;属性にのみ適用できます&#39;モジュール&#39;、 &#39;Sub&#39;、または&#39;関数&#39;宣言
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
