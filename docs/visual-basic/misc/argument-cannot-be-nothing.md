---
title: "引数には Nothing を使用できません"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrGeneral_ArgumentNullException
ms.assetid: 2abd995b-36a5-45f0-b3c1-6e0c3b31a875
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5de506c4a24f787dbb9e2d96f0e9e228f7e92288
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="argument-cannot-be-nothing"></a><span data-ttu-id="fa5ab-102">引数には Nothing を使用できません</span><span class="sxs-lookup"><span data-stu-id="fa5ab-102">Argument cannot be Nothing</span></span>
<span data-ttu-id="fa5ab-103">値が必要な引数に null 値を指定しました。</span><span class="sxs-lookup"><span data-stu-id="fa5ab-103">A null value has been supplied for an argument that must have a value.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fa5ab-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="fa5ab-104">To correct this error</span></span>  
  
-   <span data-ttu-id="fa5ab-105">オブジェクトのインスタンスを作成していない状態で、オブジェクトの使用を試みた可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fa5ab-105">You might have tried to use an object without providing an instance of the object.</span></span> <span data-ttu-id="fa5ab-106">そのような場合は、 `New` キーワードを使用してインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="fa5ab-106">In such a case, use the `New` keyword to create the instance.</span></span>  
  
-   <span data-ttu-id="fa5ab-107">値が正しく計算されることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="fa5ab-107">Check that the value is calculated correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa5ab-108">参照</span><span class="sxs-lookup"><span data-stu-id="fa5ab-108">See Also</span></span>  
 <xref:System.NullReferenceException>
