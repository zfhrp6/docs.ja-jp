---
title: "Expression recursively calls the containing property &#39;&lt;propertyname&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc42026"
  - "BC42026"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42026"
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Expression recursively calls the containing property &#39;&lt;propertyname&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロパティ定義の `Set` プロシージャ内のステートメントが、そのプロパティの名前に値を格納しています。  
  
 プロパティの値を格納するには、プロパティのコンテナーに `Private` 変数を定義し、それを `Get` プロシージャおよび `Set` プロシージャ内で使用する方法をお勧めします。  この場合は `Set` プロシージャが、この `Private` 変数に受け取った値を格納します。  
  
 `Get` プロシージャは `Function` プロシージャと同様の動作をするため、プロパティ名に値を代入したり、`End Get` ステートメントに達したときに制御を戻したりすることが可能です。  しかし、推奨されるのは、[Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) にこの値のための `Private` 変数を定義するという方法です。  
  
 `Set` プロシージャは `Sub` プロシージャと同様の動作をし、値を返しません。  したがって、プロシージャ名またはプロパティ名は、`Set` プロシージャ内では特別な意味を持たず、この名前に値を格納することはできません。  
  
 次の例は、エラーを引き起こす可能性のある方法を示しています。その後に続けて、推奨される方法を示します。  
  
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
  
 既定では、このメッセージは警告です。  警告を表示しない方法や、警告をエラーとして扱う方法の詳細については、[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic) を参照してください。  
  
 **Error ID:** BC42026  
  
### このエラーを解決するには  
  
-   上記の例で示した推奨される方法を使用するようにプロパティ定義を変更します。  
  
## 参照  
 [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)