---
title: 式を再帰的に呼び出して、包含するプロパティ &#39;&lt;propertyname&gt;&#39;です。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47de3c2d25336962168f01a4c8717274de7c9aad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a><span data-ttu-id="c5a42-102">式を再帰的に呼び出して、包含するプロパティ &#39;&lt;propertyname&gt;&#39;です。</span><span class="sxs-lookup"><span data-stu-id="c5a42-102">Expression recursively calls the containing property &#39;&lt;propertyname&gt;&#39;</span></span>
<span data-ttu-id="c5a42-103">内のステートメント、`Set`プロパティ定義のプロシージャは、プロパティの名前に、値を格納します。</span><span class="sxs-lookup"><span data-stu-id="c5a42-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="c5a42-104">定義するのには、プロパティの値を保持するための推奨アプローチ、`Private`変数、プロパティのコンテナーの両方で使用して、`Get`と`Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="c5a42-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="c5a42-105">`Set`プロシージャは、この受信した値を保存し、必要があります`Private`変数。</span><span class="sxs-lookup"><span data-stu-id="c5a42-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="c5a42-106">`Get`プロシージャの動作と同様に、`Function`プロシージャ、プロパティ名に値を代入し、戻したり制御を返す、ように、`End Get`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="c5a42-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="c5a42-107">方法をお勧め、ただし、含める、`Private`変数の値として、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="c5a42-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="c5a42-108">`Set`プロシージャの動作と同様に、`Sub`プロシージャで、値を返さない。</span><span class="sxs-lookup"><span data-stu-id="c5a42-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="c5a42-109">したがって、プロシージャまたはプロパティ名には内で特別な意味はありません、`Set`プロシージャとするに値を格納できません。</span><span class="sxs-lookup"><span data-stu-id="c5a42-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="c5a42-110">次の例は、推奨されるアプローチを続けて、このエラーを引き起こす可能性のある方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c5a42-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
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
  
 <span data-ttu-id="c5a42-111">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="c5a42-111">By default, this message is a warning.</span></span> <span data-ttu-id="c5a42-112">警告を非表示や、警告をエラーとして扱う方法の詳細についてを参照してください[Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。</span><span class="sxs-lookup"><span data-stu-id="c5a42-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c5a42-113">**エラー ID:** BC42026</span><span class="sxs-lookup"><span data-stu-id="c5a42-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c5a42-114">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c5a42-114">To correct this error</span></span>  
  
-   <span data-ttu-id="c5a42-115">前の例に示すように推奨される方法を使用するプロパティの定義を書き直してください。</span><span class="sxs-lookup"><span data-stu-id="c5a42-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a42-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5a42-116">See Also</span></span>  
 [<span data-ttu-id="c5a42-117">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="c5a42-117">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="c5a42-118">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="c5a42-118">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="c5a42-119">Set ステートメント</span><span class="sxs-lookup"><span data-stu-id="c5a42-119">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
