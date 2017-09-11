---
title: "Mid ステートメント |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MidB
- vb.Mid
dev_langs:
- VB
helpviewer_keywords:
- substrings, Mid statement
- strings [Visual Basic], substrings
- Mid statement
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e94500c8bd7f2c6351c91ba028c1ad6d8d3dd4c3
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="mid-statement"></a><span data-ttu-id="f478b-102">Mid ステートメント</span><span class="sxs-lookup"><span data-stu-id="f478b-102">Mid Statement</span></span>
<span data-ttu-id="f478b-103">指定した数の文字を置換、`String`別の文字列から文字を含む変数。</span><span class="sxs-lookup"><span data-stu-id="f478b-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f478b-104">構文</span><span class="sxs-lookup"><span data-stu-id="f478b-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="f478b-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="f478b-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="f478b-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="f478b-106">Required.</span></span> <span data-ttu-id="f478b-107">名前、`String`変数を変更します。</span><span class="sxs-lookup"><span data-stu-id="f478b-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="f478b-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="f478b-108">Required.</span></span> <span data-ttu-id="f478b-109">`Integer`式。</span><span class="sxs-lookup"><span data-stu-id="f478b-109">`Integer` expression.</span></span> <span data-ttu-id="f478b-110">文字の位置`Target`テキストの置換が開始します。</span><span class="sxs-lookup"><span data-stu-id="f478b-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="f478b-111">`Start`1 から始まるインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="f478b-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="f478b-112">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="f478b-112">Optional.</span></span> <span data-ttu-id="f478b-113">`Integer`式。</span><span class="sxs-lookup"><span data-stu-id="f478b-113">`Integer` expression.</span></span> <span data-ttu-id="f478b-114">置換する文字の数。</span><span class="sxs-lookup"><span data-stu-id="f478b-114">Number of characters to replace.</span></span> <span data-ttu-id="f478b-115">省略した場合、すべての`String`を使用します。</span><span class="sxs-lookup"><span data-stu-id="f478b-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="f478b-116">必須です。</span><span class="sxs-lookup"><span data-stu-id="f478b-116">Required.</span></span> <span data-ttu-id="f478b-117">`String`式の一部を置換する`Target`です。</span><span class="sxs-lookup"><span data-stu-id="f478b-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="f478b-118">例外</span><span class="sxs-lookup"><span data-stu-id="f478b-118">Exceptions</span></span>  
  
|<span data-ttu-id="f478b-119">例外の種類</span><span class="sxs-lookup"><span data-stu-id="f478b-119">Exception type</span></span>|<span data-ttu-id="f478b-120">条件</span><span class="sxs-lookup"><span data-stu-id="f478b-120">Condition</span></span>|  
|--------------------|---------------|  
|<span data-ttu-id="f478b-121"><xref:System.ArgumentException></xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="f478b-121"><xref:System.ArgumentException></span></span>|<span data-ttu-id="f478b-122">`Start`<= 0="" or=""></=>`Length`< 0.></ 0.></span><span class="sxs-lookup"><span data-stu-id="f478b-122">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f478b-123">コメント</span><span class="sxs-lookup"><span data-stu-id="f478b-123">Remarks</span></span>  
 <span data-ttu-id="f478b-124">置き換えられた文字の数は、文字数以下では常に`Target`します。</span><span class="sxs-lookup"><span data-stu-id="f478b-124">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="f478b-125">Visual Basic には、<xref:Microsoft.VisualBasic.Strings.Mid%2A>関数と`Mid`ステートメント</xref:Microsoft.VisualBasic.Strings.Mid%2A>。</span><span class="sxs-lookup"><span data-stu-id="f478b-125">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="f478b-126">この要素はどちらも、文字列内の文字の指定の数が、`Mid`関数の中に文字を返します、`Mid`文字をステートメントに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f478b-126">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="f478b-127">詳細については、 <xref:Microsoft.VisualBasic.Strings.Mid%2A>。</xref:Microsoft.VisualBasic.Strings.Mid%2A>を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f478b-127">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f478b-128">`MidB`以前のバージョンの Visual Basic のステートメントには、文字ではなく、(バイト単位) の部分文字列が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="f478b-128">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="f478b-129">2 バイト文字セット (DBCS) のアプリケーションで文字列に変換するためには、主に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f478b-129">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="f478b-130">Visual Basic のすべての文字列が Unicode と`MidB`現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f478b-130">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f478b-131">例</span><span class="sxs-lookup"><span data-stu-id="f478b-131">Example</span></span>  
 <span data-ttu-id="f478b-132">この例では、`Mid`ステートメントに指定した文字列変数の文字数を別の文字列から文字に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f478b-132">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 <span data-ttu-id="f478b-133">[!code-vb[VbVbalrStrings&#5;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f478b-133">[!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f478b-134">要件</span><span class="sxs-lookup"><span data-stu-id="f478b-134">Requirements</span></span>  
 <span data-ttu-id="f478b-135">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="f478b-135">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="f478b-136">**モジュール:**`Strings`</span><span class="sxs-lookup"><span data-stu-id="f478b-136">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="f478b-137">**アセンブリ:**[!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime_md.md)]</span><span class="sxs-lookup"><span data-stu-id="f478b-137">**Assembly:** [!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime_md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f478b-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="f478b-138">See Also</span></span>  
 <span data-ttu-id="f478b-139"><xref:Microsoft.VisualBasic.Strings.Mid%2A></xref:Microsoft.VisualBasic.Strings.Mid%2A></span><span class="sxs-lookup"><span data-stu-id="f478b-139"><xref:Microsoft.VisualBasic.Strings.Mid%2A></span></span>   
<span data-ttu-id="f478b-140"> [文字列](../../../visual-basic/programming-guide/language-features/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="f478b-140"> [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md) </span></span>  
<span data-ttu-id="f478b-141"> [Visual Basic における文字列の概要](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)</span><span class="sxs-lookup"><span data-stu-id="f478b-141"> [Introduction to Strings in Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)</span></span>
