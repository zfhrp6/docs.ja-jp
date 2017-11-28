---
title: "&#39;です。モジュール &#39;ステートメントは、ファイルまたは名前空間レベルでのみ発生することができます。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords: BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61fe12fbd7d20e6cd2b6bc464e7fc3293150213b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="0363e-102">&#39;です。モジュール &#39;ステートメントは、ファイルまたは名前空間レベルでのみ発生することができます。</span><span class="sxs-lookup"><span data-stu-id="0363e-102">&#39;Module&#39; statements can occur only at file or namespace level</span></span>
<span data-ttu-id="0363e-103">`Module`ステートメントが、ソース ファイルの上部に表示する必要がありますの直後に`Option`と`Imports`ステートメント、グローバル属性、および名前空間宣言が、その他のすべての宣言の前にします。</span><span class="sxs-lookup"><span data-stu-id="0363e-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="0363e-104">**エラー ID:** BC30617</span><span class="sxs-lookup"><span data-stu-id="0363e-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0363e-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0363e-105">To correct this error</span></span>  
  
-   <span data-ttu-id="0363e-106">移動、`Module`名前空間の宣言またはソース ファイルの先頭にステートメントです。</span><span class="sxs-lookup"><span data-stu-id="0363e-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0363e-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="0363e-107">See Also</span></span>  
 [<span data-ttu-id="0363e-108">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="0363e-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
