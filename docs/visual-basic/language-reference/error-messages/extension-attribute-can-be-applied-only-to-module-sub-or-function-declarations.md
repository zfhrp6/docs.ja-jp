---
title: "&quot;Extension&quot; 属性は &quot;Module&quot;、&quot;Sub&quot; または &quot;Function&quot; の宣言にのみ適用できます。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36550
- vbc36550
dev_langs:
- VB
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3eee008f737bf625023b6e4d58e1df7d282148d3
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>'Extension' 属性は 'Module'、'Sub' または 'Function' の宣言にのみ適用できます。
Visual Basic でのデータ型を拡張する唯一の方法では、標準のモジュール内の拡張メソッドを定義します。 拡張メソッドになる、`Sub`プロシージャまたは`Function`プロシージャです。 すべての拡張メソッドは、拡張属性でマークする必要があります`<Extension()>`から、<xref:System.Runtime.CompilerServices?displayProperty=fullName>名前空間</xref:System.Runtime.CompilerServices?displayProperty=fullName>。 必要に応じて、拡張メソッドを格納しているモジュールの場合は、同じ方法でマークされている可能性があります。 拡張属性の他の使用が有効ではありません。  
  
 **エラー ID:** BC36550  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   拡張属性を削除します。  
  
-   外側のモジュールで定義されている、方法として、拡張機能を設計し直します。  
  
## <a name="example"></a>例  
 次の例、`Print`のメソッド、`String`データ型。  
  
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

