---
title: 変数&#39; &lt;variablename&gt; &#39;それを囲むブロック内の変数を非表示になります
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 58e09caeb477d6b1df7f3be17e0a8ee05be3551e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595093"
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="f3cba-102">変数&#39; &lt;variablename&gt; &#39;それを囲むブロック内の変数を非表示になります</span><span class="sxs-lookup"><span data-stu-id="f3cba-102">Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block</span></span>
<span data-ttu-id="f3cba-103">ブロックで囲まれた変数では、別のローカル変数と同じ名前を持っています。</span><span class="sxs-lookup"><span data-stu-id="f3cba-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="f3cba-104">**エラー ID:** BC30616</span><span class="sxs-lookup"><span data-stu-id="f3cba-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f3cba-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="f3cba-105">To correct this error</span></span>  
  
-   <span data-ttu-id="f3cba-106">囲まれたブロック内の変数の名前を変更して、その他のローカル変数と同じではないようにします。</span><span class="sxs-lookup"><span data-stu-id="f3cba-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="f3cba-107">例えば:</span><span class="sxs-lookup"><span data-stu-id="f3cba-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="f3cba-108">このエラーの一般的な原因は、使用する`Catch e As Exception`イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="f3cba-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="f3cba-109">大文字と小文字の場合は、名前、`Catch`ブロック変数`ex`なく`e`です。</span><span class="sxs-lookup"><span data-stu-id="f3cba-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="f3cba-110">このエラーのもう 1 つの一般的な原因は内で宣言されたローカル変数へのアクセスに、`Try`別個のブロック`Catch`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="f3cba-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="f3cba-111">これを修正するには、外部変数を宣言、`Try...Catch...Finally`構造体。</span><span class="sxs-lookup"><span data-stu-id="f3cba-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3cba-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3cba-112">See Also</span></span>  
 [<span data-ttu-id="f3cba-113">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="f3cba-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="f3cba-114">変数宣言</span><span class="sxs-lookup"><span data-stu-id="f3cba-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
