---
title: "プロパティ &quot;&lt;propertyname&gt;&quot; すべてのコード パスで値が返されない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
dev_langs:
- VB
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: 7
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
ms.openlocfilehash: 64bacc2a2494160b3f9bbaec0915179f40735ef0
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="dcd30-102">プロパティ '&lt;propertyname&gt;' すべてのコード パスで値が返されない</span><span class="sxs-lookup"><span data-stu-id="dcd30-102">Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="dcd30-103">プロパティ '\<propertyname >' すべてのコード パスで値を返しません。</span><span class="sxs-lookup"><span data-stu-id="dcd30-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="dcd30-104">この結果が使用されると、実行時に Null 参照例外が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dcd30-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="dcd30-105">プロパティ`Get`手順では、値を返さないことをコードから少なくとも&1; つの可能なパスです。</span><span class="sxs-lookup"><span data-stu-id="dcd30-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="dcd30-106">プロパティから値を返すことができます`Get`次の方法のいずれかの手順。</span><span class="sxs-lookup"><span data-stu-id="dcd30-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="dcd30-107">プロパティ名に値を代入し、実行、`Exit Property`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="dcd30-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
-   <span data-ttu-id="dcd30-108">プロパティ名に値を代入し、実行、`End Get`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="dcd30-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
-   <span data-ttu-id="dcd30-109">値を含む、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="dcd30-109">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="dcd30-110">制御が移るかどうか`Exit Property`または`End Get`プロパティ名に任意の値が割り当てられていないと、`Get`プロパティのデータ型の既定値を返します。</span><span class="sxs-lookup"><span data-stu-id="dcd30-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="dcd30-111">詳細については、「動作」を参照してください[Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="dcd30-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="dcd30-112">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="dcd30-112">By default, this message is a warning.</span></span> <span data-ttu-id="dcd30-113">警告を非表示や警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="dcd30-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="dcd30-114">**エラー ID:** BC42107</span><span class="sxs-lookup"><span data-stu-id="dcd30-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dcd30-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="dcd30-115">To correct this error</span></span>  
  
-   <span data-ttu-id="dcd30-116">制御フローのロジックを確認し、すべてのステートメントが値を返す前に値を代入するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="dcd30-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="dcd30-117">常に使用する場合に、プロシージャからリターンごとに値を返すことを保証する方が簡単、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="dcd30-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="dcd30-118">この場合、最後のステートメントの前に`End Get`する必要があります、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="dcd30-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcd30-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcd30-119">See Also</span></span>  
 <span data-ttu-id="dcd30-120">[プロパティ プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="dcd30-120">[Property Procedures](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) </span></span>  
<span data-ttu-id="dcd30-121"> [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="dcd30-121"> [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="dcd30-122"> [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)</span><span class="sxs-lookup"><span data-stu-id="dcd30-122"> [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)</span></span>
