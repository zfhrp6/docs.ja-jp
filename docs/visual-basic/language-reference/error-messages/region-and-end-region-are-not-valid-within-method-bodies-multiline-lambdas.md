---
title: '&#39;#Region&#39;と&#39;#End Region&#39;ステートメントはメソッド本体に複数行ラムダでは有効ではありません。'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: bf3843e0ec3009f3dc7d60e91c340a7f20543231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593234"
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="4ae9a-102">&#39;#Region&#39;と&#39;#End Region&#39;ステートメントはメソッド本体や複数行ラムダでは有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="4ae9a-102">&#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="4ae9a-103">`#Region`ブロックは、クラス、モジュール、または名前空間レベルで宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ae9a-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="4ae9a-104">折りたたみ可能な領域が 1 つ以上のプロシージャを含めることができますが、開始日または終了、プロシージャ内でそのことはできません。</span><span class="sxs-lookup"><span data-stu-id="4ae9a-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="4ae9a-105">**エラー ID:** BC32025</span><span class="sxs-lookup"><span data-stu-id="4ae9a-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4ae9a-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4ae9a-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="4ae9a-107">前の手順がで正常終了したことを確認してください、`End Function`または`End Sub`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4ae9a-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="4ae9a-108">いることを確認、`#Region`と`#End Region`ディレクティブが同じコード ブロックではします。</span><span class="sxs-lookup"><span data-stu-id="4ae9a-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae9a-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ae9a-109">See Also</span></span>  
 [<span data-ttu-id="4ae9a-110">#Region ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="4ae9a-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
