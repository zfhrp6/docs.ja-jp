---
title: "定義クラスのインスタンスではないオブジェクトのフレンド関数は呼び出せません"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f1ac1ea14efb0cdf0d8ca03257e4da33d35e368
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="f088d-102">定義クラスのインスタンスではないオブジェクトのフレンド関数は呼び出せません</span><span class="sxs-lookup"><span data-stu-id="f088d-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="f088d-103">クラスの `Friend` プロシージャを呼び出そうとするか、プロセス間またはスレッド間で `Friend` プロパティまたはメソッドにアクセスしようとしました。</span><span class="sxs-lookup"><span data-stu-id="f088d-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="f088d-104">`Friend` 手順はクラスの外部のモジュールから呼び出せますが、クラスが定義されているプロジェクトの一部です。</span><span class="sxs-lookup"><span data-stu-id="f088d-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f088d-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="f088d-105">To correct this error</span></span>  
  
-   <span data-ttu-id="f088d-106">クラスが定義されているプロジェクトの一部であるモジュールからプロシージャを呼び出しているか、またはアクセスしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f088d-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f088d-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="f088d-107">See Also</span></span>  
 [<span data-ttu-id="f088d-108">Friend</span><span class="sxs-lookup"><span data-stu-id="f088d-108">Friend</span></span>](../../visual-basic/language-reference/modifiers/friend.md)
