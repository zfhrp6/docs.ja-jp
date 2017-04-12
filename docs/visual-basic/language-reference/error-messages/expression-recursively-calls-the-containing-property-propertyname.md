---
title: "式を再帰的には、包含するプロパティを呼び出して &quot;&lt;propertyname&gt;&quot; |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42026
- BC42026
dev_langs:
- VB
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
caps.latest.revision: 10
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ca20bf1a539f2727a80f8e781c1e9ebc5a4a253d
ms.lasthandoff: 03/13/2017

---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a>式を再帰的には、包含するプロパティを呼び出して '&lt;propertyname&gt;'
内のステートメント、`Set`プロパティ定義のプロシージャは、プロパティの名前に、値を格納します。  
  
 プロパティの値を保持するための推奨アプローチを定義するのには、`Private`プロパティのコンテナーに変数が両方でそれを使用して、`Get`と`Set`プロシージャです。 `Set`プロシージャは、この受信した値を格納し、必要があります`Private`変数です。  
  
 `Get`のようにプロシージャの動作、`Function`プロシージャ、プロパティ名に値を代入し、発生して、制御を返すように、`End Get`ステートメントです。 推奨される方法に含める、`Private`変数の値として、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)します。  
  
 `Set`のようにプロシージャの動作、`Sub`値を返さないプロシージャです。 したがって、プロシージャまたはプロパティの名前、特別な意味を持ちません内で、`Set`しする手順は、そこに値を格納ことはできません。  
  
 次の例は、推奨されるアプローチを続けて、このエラーを引き起こす可能性のある方法を示しています。  
  
```  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 既定では、このメッセージは警告です。 警告を非表示や警告をエラーとして扱う方法の詳細については、次を参照してください[Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。  
  
 **エラー ID:** BC42026  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   前の例に示すように推奨されるアプローチを使用するプロパティの定義を書き直してください。  
  
## <a name="see-also"></a>関連項目  
 [プロパティ プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)
