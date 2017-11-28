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
ms.openlocfilehash: 3a54cf0ed9e2b307174c1be0e853a920dfc94202
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="argument-cannot-be-nothing"></a><span data-ttu-id="a384b-102">引数には Nothing を使用できません</span><span class="sxs-lookup"><span data-stu-id="a384b-102">Argument cannot be Nothing</span></span>
<span data-ttu-id="a384b-103">値が必要な引数に null 値を指定しました。</span><span class="sxs-lookup"><span data-stu-id="a384b-103">A null value has been supplied for an argument that must have a value.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a384b-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="a384b-104">To correct this error</span></span>  
  
-   <span data-ttu-id="a384b-105">オブジェクトのインスタンスを作成していない状態で、オブジェクトの使用を試みた可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a384b-105">You might have tried to use an object without providing an instance of the object.</span></span> <span data-ttu-id="a384b-106">そのような場合は、 `New` キーワードを使用してインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="a384b-106">In such a case, use the `New` keyword to create the instance.</span></span>  
  
-   <span data-ttu-id="a384b-107">値が正しく計算されることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a384b-107">Check that the value is calculated correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a384b-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="a384b-108">See Also</span></span>  
 [<span data-ttu-id="a384b-109">例外のトラブルシューティング : System.NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="a384b-109">Troubleshooting Exceptions: System.NullReferenceException</span></span>](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
