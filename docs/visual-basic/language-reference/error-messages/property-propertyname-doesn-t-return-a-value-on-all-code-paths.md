---
title: プロパティ&#39; &lt;propertyname&gt; &#39;しません&#39;t は、すべてのコード パスで値を返しません
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 72bc7e45cadd2528f29c88bf6e80ee5f381052dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594215"
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="54acc-102">プロパティ&#39; &lt;propertyname&gt; &#39;しません&#39;t は、すべてのコード パスで値を返しません</span><span class="sxs-lookup"><span data-stu-id="54acc-102">Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="54acc-103">プロパティ '\<propertyname >' は、すべてのコード パスで値を返しません。</span><span class="sxs-lookup"><span data-stu-id="54acc-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="54acc-104">この結果が使用されると、実行時に Null 参照例外が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="54acc-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="54acc-105">プロパティ`Get`手順では、値を返さないコードに少なくとも 1 つの可能なパスです。</span><span class="sxs-lookup"><span data-stu-id="54acc-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="54acc-106">プロパティから値を返すことができます`Get`次の方法のいずれかの手順。</span><span class="sxs-lookup"><span data-stu-id="54acc-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="54acc-107">プロパティ名に値を代入し、実行、`Exit Property`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="54acc-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
-   <span data-ttu-id="54acc-108">プロパティ名に値を代入し、実行、`End Get`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="54acc-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
-   <span data-ttu-id="54acc-109">値を含む、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="54acc-109">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="54acc-110">コントロールに渡します`Exit Property`または`End Get`プロパティ名の後に任意の値が割り当てられていないと、`Get`プロシージャ、プロパティのデータ型の既定値を返します。</span><span class="sxs-lookup"><span data-stu-id="54acc-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="54acc-111">詳細については、「動作」を参照してください[関数ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="54acc-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="54acc-112">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="54acc-112">By default, this message is a warning.</span></span> <span data-ttu-id="54acc-113">警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。</span><span class="sxs-lookup"><span data-stu-id="54acc-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="54acc-114">**エラー ID:** BC42107</span><span class="sxs-lookup"><span data-stu-id="54acc-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="54acc-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="54acc-115">To correct this error</span></span>  
  
-   <span data-ttu-id="54acc-116">制御フローのロジックを確認し、戻り値の原因となるすべてのステートメントの前に値を代入するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="54acc-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="54acc-117">すべてを返すプロシージャが常に使用する場合に、値を返すことを保証しやすく、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="54acc-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="54acc-118">この場合、最後のステートメントの前に`End Get`する必要があります、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="54acc-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54acc-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="54acc-119">See Also</span></span>  
 [<span data-ttu-id="54acc-120">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="54acc-120">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="54acc-121">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="54acc-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="54acc-122">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="54acc-122">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
