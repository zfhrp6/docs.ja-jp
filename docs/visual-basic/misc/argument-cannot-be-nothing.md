---
title: 引数には Nothing を使用できません
ms.date: 07/20/2015
f1_keywords:
- vbrGeneral_ArgumentNullException
ms.assetid: 2abd995b-36a5-45f0-b3c1-6e0c3b31a875
ms.openlocfilehash: 7b08dd41f638138df4c2f92fbe9f05f1312c2d03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600070"
---
# <a name="argument-cannot-be-nothing"></a><span data-ttu-id="b89df-102">引数には Nothing を使用できません</span><span class="sxs-lookup"><span data-stu-id="b89df-102">Argument cannot be Nothing</span></span>
<span data-ttu-id="b89df-103">値が必要な引数に null 値を指定しました。</span><span class="sxs-lookup"><span data-stu-id="b89df-103">A null value has been supplied for an argument that must have a value.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b89df-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b89df-104">To correct this error</span></span>  
  
-   <span data-ttu-id="b89df-105">オブジェクトのインスタンスを作成していない状態で、オブジェクトの使用を試みた可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b89df-105">You might have tried to use an object without providing an instance of the object.</span></span> <span data-ttu-id="b89df-106">そのような場合は、 `New` キーワードを使用してインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b89df-106">In such a case, use the `New` keyword to create the instance.</span></span>  
  
-   <span data-ttu-id="b89df-107">値が正しく計算されることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b89df-107">Check that the value is calculated correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b89df-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="b89df-108">See Also</span></span>  
 <xref:System.NullReferenceException>
