---
title: "コールバック関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 84c3f13317f771ba81af0fc7368124c59f8a1a37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="callback-functions"></a><span data-ttu-id="db5bf-102">コールバック関数</span><span class="sxs-lookup"><span data-stu-id="db5bf-102">Callback Functions</span></span>
<span data-ttu-id="db5bf-103">コールバック関数は、アンマネージ DLL 関数がタスクを完了できるように支援するマネージ アプリケーション内のコードです。</span><span class="sxs-lookup"><span data-stu-id="db5bf-103">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="db5bf-104">コールバック関数の呼び出しは、マネージ アプリケーションから、DLL 関数を介して、マネージ実装へと間接的に渡されます。</span><span class="sxs-lookup"><span data-stu-id="db5bf-104">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="db5bf-105">多数ある DLL 関数の一部はプラットフォーム呼び出しと呼ばれ、正常に実行されるには、マネージ コード内にコールバック関数が必要です。</span><span class="sxs-lookup"><span data-stu-id="db5bf-105">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="db5bf-106">ほとんどの DLL 関数は、マネージ コードから呼び出す場合、関数のマネージ定義を作成してから、それを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="db5bf-106">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="db5bf-107">このプロセスは簡単です。</span><span class="sxs-lookup"><span data-stu-id="db5bf-107">The process is straightforward.</span></span>  
  
 <span data-ttu-id="db5bf-108">コールバック関数を必要とする DLL 関数を使用する場合は、追加の手順がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="db5bf-108">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="db5bf-109">まず、関数のドキュメントを参照して、その関数にコールバックが必要かどうかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db5bf-109">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="db5bf-110">次に、マネージ アプリケーションにコールバック関数を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db5bf-110">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="db5bf-111">最後に、DLL 関数を呼び出し、引数としてコールバック関数のポインターを渡します。</span><span class="sxs-lookup"><span data-stu-id="db5bf-111">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span> <span data-ttu-id="db5bf-112">次の図は、この手順をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="db5bf-112">The following illustration summarizes these steps.</span></span>  
  
 <span data-ttu-id="db5bf-113">![プラットフォーム呼び出しコールバック](../../../docs/framework/interop/media/pinvokecallback.gif "pinvokecallback")</span><span class="sxs-lookup"><span data-stu-id="db5bf-113">![Platform invoke callback](../../../docs/framework/interop/media/pinvokecallback.gif "pinvokecallback")</span></span>  
<span data-ttu-id="db5bf-114">コールバック関数と実装</span><span class="sxs-lookup"><span data-stu-id="db5bf-114">Callback function and implementation</span></span>  
  
 <span data-ttu-id="db5bf-115">コールバック関数は、タスクが繰り返し実行される状況での使用に最適です。</span><span class="sxs-lookup"><span data-stu-id="db5bf-115">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="db5bf-116">また、一般的な用途として、Win32 API の **EnumFontFamilies**、**EnumPrinters**、**EnumWindows** などの列挙関数があります。</span><span class="sxs-lookup"><span data-stu-id="db5bf-116">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Win32 API.</span></span> <span data-ttu-id="db5bf-117">**EnumWindows** 関数は、各ウィンドウでタスクを実行するコールバック関数を呼び出して、コンピューター上のすべての既存のウィンドウを列挙します。</span><span class="sxs-lookup"><span data-stu-id="db5bf-117">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="db5bf-118">手順と例については、「[How to: Implement Callback Functions](../../../docs/framework/interop/how-to-implement-callback-functions.md)」(方法: コールバック関数を実装する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db5bf-118">For instructions and an example, see [How to: Implement Callback Functions](../../../docs/framework/interop/how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db5bf-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="db5bf-119">See Also</span></span>  
 [<span data-ttu-id="db5bf-120">方法: コールバック関数を実装する</span><span class="sxs-lookup"><span data-stu-id="db5bf-120">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 [<span data-ttu-id="db5bf-121">DLL 関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="db5bf-121">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
