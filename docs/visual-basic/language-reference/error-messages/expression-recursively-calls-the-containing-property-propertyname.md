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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c7168ab2a2ec5eb0c0d423120b67c10b117c14b2
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a><span data-ttu-id="bf139-102">式を再帰的には、包含するプロパティを呼び出して '&lt;propertyname&gt;'</span><span class="sxs-lookup"><span data-stu-id="bf139-102">Expression recursively calls the containing property &#39;&lt;propertyname&gt;&#39;</span></span>
<span data-ttu-id="bf139-103">内のステートメント、`Set`プロパティ定義のプロシージャは、プロパティの名前に、値を格納します。</span><span class="sxs-lookup"><span data-stu-id="bf139-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="bf139-104">プロパティの値を保持するための推奨アプローチを定義するのには、`Private`プロパティのコンテナーに変数が両方でそれを使用して、`Get`と`Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="bf139-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="bf139-105">`Set`プロシージャは、この受信した値を格納し、必要があります`Private`変数です。</span><span class="sxs-lookup"><span data-stu-id="bf139-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="bf139-106">`Get`のようにプロシージャの動作、`Function`プロシージャ、プロパティ名に値を代入し、発生して、制御を返すように、`End Get`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="bf139-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="bf139-107">推奨される方法に含める、`Private`変数の値として、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="bf139-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="bf139-108">`Set`のようにプロシージャの動作、`Sub`値を返さないプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="bf139-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="bf139-109">したがって、プロシージャまたはプロパティの名前、特別な意味を持ちません内で、`Set`しする手順は、そこに値を格納ことはできません。</span><span class="sxs-lookup"><span data-stu-id="bf139-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="bf139-110">次の例は、推奨されるアプローチを続けて、このエラーを引き起こす可能性のある方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bf139-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
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
  
 <span data-ttu-id="bf139-111">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="bf139-111">By default, this message is a warning.</span></span> <span data-ttu-id="bf139-112">警告を非表示や警告をエラーとして扱う方法の詳細については、次を参照してください[Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="bf139-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="bf139-113">**エラー ID:** BC42026</span><span class="sxs-lookup"><span data-stu-id="bf139-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bf139-114">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="bf139-114">To correct this error</span></span>  
  
-   <span data-ttu-id="bf139-115">前の例に示すように推奨されるアプローチを使用するプロパティの定義を書き直してください。</span><span class="sxs-lookup"><span data-stu-id="bf139-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf139-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf139-116">See Also</span></span>  
 <span data-ttu-id="bf139-117">[プロパティ プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="bf139-117">[Property Procedures](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) </span></span>  
<span data-ttu-id="bf139-118"> [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="bf139-118"> [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="bf139-119"> [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)</span><span class="sxs-lookup"><span data-stu-id="bf139-119"> [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)</span></span>
