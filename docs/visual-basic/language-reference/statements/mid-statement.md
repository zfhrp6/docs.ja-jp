---
title: Mid ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: 90b805df902dcdfebe85421583dd54e9af04bec9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602266"
---
# <a name="mid-statement"></a><span data-ttu-id="0f61b-102">Mid ステートメント</span><span class="sxs-lookup"><span data-stu-id="0f61b-102">Mid Statement</span></span>
<span data-ttu-id="0f61b-103">指定した数の文字を置換、`String`別の文字列から文字を含む変数。</span><span class="sxs-lookup"><span data-stu-id="0f61b-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f61b-104">構文</span><span class="sxs-lookup"><span data-stu-id="0f61b-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="0f61b-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="0f61b-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="0f61b-106">必須。</span><span class="sxs-lookup"><span data-stu-id="0f61b-106">Required.</span></span> <span data-ttu-id="0f61b-107">名前、`String`変数を変更します。</span><span class="sxs-lookup"><span data-stu-id="0f61b-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="0f61b-108">必須。</span><span class="sxs-lookup"><span data-stu-id="0f61b-108">Required.</span></span> <span data-ttu-id="0f61b-109">`Integer` 式。</span><span class="sxs-lookup"><span data-stu-id="0f61b-109">`Integer` expression.</span></span> <span data-ttu-id="0f61b-110">文字の位置`Target`テキストの置換を開始します。</span><span class="sxs-lookup"><span data-stu-id="0f61b-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="0f61b-111">`Start` 1 から始まるインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="0f61b-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="0f61b-112">任意。</span><span class="sxs-lookup"><span data-stu-id="0f61b-112">Optional.</span></span> <span data-ttu-id="0f61b-113">`Integer` 式。</span><span class="sxs-lookup"><span data-stu-id="0f61b-113">`Integer` expression.</span></span> <span data-ttu-id="0f61b-114">置換する文字の数。</span><span class="sxs-lookup"><span data-stu-id="0f61b-114">Number of characters to replace.</span></span> <span data-ttu-id="0f61b-115">省略した場合、すべての`String`を使用します。</span><span class="sxs-lookup"><span data-stu-id="0f61b-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="0f61b-116">必須。</span><span class="sxs-lookup"><span data-stu-id="0f61b-116">Required.</span></span> <span data-ttu-id="0f61b-117">`String` 式の一部を置換する`Target`です。</span><span class="sxs-lookup"><span data-stu-id="0f61b-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="0f61b-118">例外</span><span class="sxs-lookup"><span data-stu-id="0f61b-118">Exceptions</span></span>  
  
|<span data-ttu-id="0f61b-119">例外の種類</span><span class="sxs-lookup"><span data-stu-id="0f61b-119">Exception type</span></span>|<span data-ttu-id="0f61b-120">条件</span><span class="sxs-lookup"><span data-stu-id="0f61b-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="0f61b-121">`Start` < = 0 または`Length`< 0 です。</span><span class="sxs-lookup"><span data-stu-id="0f61b-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f61b-122">コメント</span><span class="sxs-lookup"><span data-stu-id="0f61b-122">Remarks</span></span>  
 <span data-ttu-id="0f61b-123">置換される文字数は、の文字数以下では常に`Target`です。</span><span class="sxs-lookup"><span data-stu-id="0f61b-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="0f61b-124">Visual Basic には、<xref:Microsoft.VisualBasic.Strings.Mid%2A>関数と`Mid`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="0f61b-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="0f61b-125">この要素はどちらも、文字列の文字の指定された数が、`Mid`関数の中に文字を返します、`Mid`文字をステートメントに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0f61b-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="0f61b-126">詳細については、「<xref:Microsoft.VisualBasic.Strings.Mid%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f61b-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f61b-127">`MidB`以前のバージョンの Visual Basic のステートメントには文字ではなく、(バイト単位) 内の部分文字列が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="0f61b-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="0f61b-128">2 バイト文字セット (DBCS) のアプリケーションで文字列を変換するため、主に使用されます。</span><span class="sxs-lookup"><span data-stu-id="0f61b-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="0f61b-129">Unicode では、すべての Visual Basic の文字列と`MidB`は現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="0f61b-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f61b-130">例</span><span class="sxs-lookup"><span data-stu-id="0f61b-130">Example</span></span>  
 <span data-ttu-id="0f61b-131">この例では、`Mid`ステートメントに指定した文字列変数の文字数を別の文字列から文字に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0f61b-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="0f61b-132">要件</span><span class="sxs-lookup"><span data-stu-id="0f61b-132">Requirements</span></span>  
 <span data-ttu-id="0f61b-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="0f61b-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="0f61b-134">**モジュール:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="0f61b-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="0f61b-135">**アセンブリ:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f61b-135">**Assembly:** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f61b-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f61b-136">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [<span data-ttu-id="0f61b-137">文字列</span><span class="sxs-lookup"><span data-stu-id="0f61b-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="0f61b-138">Visual Basic の文字列の概要</span><span class="sxs-lookup"><span data-stu-id="0f61b-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
