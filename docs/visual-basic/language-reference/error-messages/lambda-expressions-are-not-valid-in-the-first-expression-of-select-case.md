---
title: ラムダ式での最初の式では有効ではありません、 &#39;Select Case&#39;ステートメント
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: c492615850ec089fe35c1ae4eaba90a741e30f42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588922"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a><span data-ttu-id="ba175-102">ラムダ式での最初の式では有効ではありません、 &#39;Select Case&#39;ステートメント</span><span class="sxs-lookup"><span data-stu-id="ba175-102">Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement</span></span>
<span data-ttu-id="ba175-103">テスト式でのラムダ式を使用することはできません、`Select Case`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ba175-103">You cannot use a lambda expression for the test expression in a `Select Case` statement.</span></span> <span data-ttu-id="ba175-104">ラムダ式の定義を返す関数、およびのテスト式、`Select Case`ステートメントは、基本データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba175-104">Lambda expression definitions return functions, and the test expression of a `Select Case` statement must be an elementary data type.</span></span>  
  
 <span data-ttu-id="ba175-105">次のコードでは、このエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ba175-105">The following code causes this error:</span></span>  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 <span data-ttu-id="ba175-106">**エラー ID:** BC36635</span><span class="sxs-lookup"><span data-stu-id="ba175-106">**Error ID:** BC36635</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ba175-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="ba175-107">To correct this error</span></span>  
  
-   <span data-ttu-id="ba175-108">コードを調べて、 `If...Then...Else` ステートメントなどの別の条件構造を使用できないかをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="ba175-108">Examine your code to determine whether a different conditional construction, such as an `If...Then...Else` statement, would work for you.</span></span>  
  
-   <span data-ttu-id="ba175-109">指定したこの関数を呼び出して、次のコードに示すように。</span><span class="sxs-lookup"><span data-stu-id="ba175-109">You may have intended to call the function, as shown in the following code:</span></span>  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba175-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba175-110">See Also</span></span>  
 [<span data-ttu-id="ba175-111">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="ba175-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="ba175-112">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="ba175-112">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="ba175-113">Select...Case ステートメント</span><span class="sxs-lookup"><span data-stu-id="ba175-113">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
