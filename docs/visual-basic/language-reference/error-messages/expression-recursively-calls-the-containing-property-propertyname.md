---
title: 式を再帰的には、包含するプロパティを呼び出して&#39; &lt;propertyname&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: f14e2645772b22a8f6ff2385dcd316a42d1d5cf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588844"
---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a>式を再帰的には、包含するプロパティを呼び出して&#39; &lt;propertyname&gt;&#39;
内のステートメント、`Set`プロパティ定義のプロシージャは、プロパティの名前に、値を格納します。  
  
 定義するのには、プロパティの値を保持するための推奨アプローチ、`Private`変数、プロパティのコンテナーの両方で使用して、`Get`と`Set`プロシージャです。 `Set`プロシージャは、この受信した値を保存し、必要があります`Private`変数。  
  
 `Get`プロシージャの動作と同様に、`Function`プロシージャ、プロパティ名に値を代入し、戻したり制御を返す、ように、`End Get`ステートメントです。 方法をお勧め、ただし、含める、`Private`変数の値として、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)です。  
  
 `Set`プロシージャの動作と同様に、`Sub`プロシージャで、値を返さない。 したがって、プロシージャまたはプロパティ名には内で特別な意味はありません、`Set`プロシージャとするに値を格納できません。  
  
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
  
 既定では、このメッセージは警告です。 警告を非表示や、警告をエラーとして扱う方法の詳細についてを参照してください[Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。  
  
 **エラー ID:** BC42026  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   前の例に示すように推奨される方法を使用するプロパティの定義を書き直してください。  
  
## <a name="see-also"></a>関連項目  
 [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)
