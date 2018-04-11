---
title: 引数は省略できません。(Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID449
ms.assetid: 76e7bcf3-24ed-4cd5-945b-b98f1c76944b
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 91cc5bc90e226a36f4afe6ccc250dfe28ead5b5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="argument-not-optional-visual-basic"></a><span data-ttu-id="90e60-102">引数は省略できません。(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90e60-102">Argument not optional (Visual Basic)</span></span>
<span data-ttu-id="90e60-103">引数の型と数は、予測されると一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="90e60-103">The number and types of arguments must match those expected.</span></span> <span data-ttu-id="90e60-104">引数の数が正しくないか、省略された引数は省略できません。</span><span class="sxs-lookup"><span data-stu-id="90e60-104">Either there is an incorrect number of arguments, or an omitted argument is not optional.</span></span> <span data-ttu-id="90e60-105">宣言されている場合、引数をユーザー定義プロシージャの呼び出しから省略のみできます`Optional`プロシージャの定義でします。</span><span class="sxs-lookup"><span data-stu-id="90e60-105">An argument can only be omitted from a call to a user-defined procedure if it was declared `Optional` in the procedure definition.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="90e60-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="90e60-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="90e60-107">すべての必要な引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="90e60-107">Supply all necessary arguments.</span></span>  
  
2.  <span data-ttu-id="90e60-108">省略された引数は省略可能なことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="90e60-108">Make sure omitted arguments are optional.</span></span> <span data-ttu-id="90e60-109">間違っている場合、呼び出しで引数を指定するか、パラメーターを宣言`Optional`定義します。</span><span class="sxs-lookup"><span data-stu-id="90e60-109">If they are not, either supply the argument in the call, or declare the parameter `Optional` in the definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e60-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="90e60-110">See Also</span></span>  
 [<span data-ttu-id="90e60-111">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="90e60-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
