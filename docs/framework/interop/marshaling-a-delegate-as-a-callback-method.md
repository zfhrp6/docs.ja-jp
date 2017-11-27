---
title: "コールバック メソッドとしてのデリゲートのマーシャ リング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c8c4eca35c406b38da603dc10358920ee887b137
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="dfc46-102">コールバック メソッドとしてのデリゲートのマーシャ リング</span><span class="sxs-lookup"><span data-stu-id="dfc46-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="dfc46-103">このサンプルでは、関数ポインターを要求するアンマネージ関数にデリゲートを渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dfc46-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="dfc46-104">デリゲートは、メソッドへの参照を保持できるクラスであり、タイプ セーフな関数ポインターまたはコールバック関数と同等のものです。</span><span class="sxs-lookup"><span data-stu-id="dfc46-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dfc46-105">呼び出しの中でデリゲートを使うと、共通言語ランタイムがデリゲートをその呼び出しの期間中ガベージ コレクションから保護します。</span><span class="sxs-lookup"><span data-stu-id="dfc46-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="dfc46-106">ただし、アンマネージ関数が呼び出し完了後に使うためにデリゲートを保存する場合は、アンマネージ関数がデリゲートを終了するまで手動でガベージ コレクションを防ぐ必要があります。</span><span class="sxs-lookup"><span data-stu-id="dfc46-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="dfc46-107">詳細については、「[HandleRef Sample](http://msdn.microsoft.com/en-us/ab23b04e-1d53-4ec7-b27a-e892d9298959)」(HandleRef のサンプル) および「[GCHandle Sample](http://msdn.microsoft.com/en-us/6acce798-0385-4ded-a790-77da842c113f)」(GCHandle のサンプル) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dfc46-107">For more information, see the [HandleRef Sample](http://msdn.microsoft.com/en-us/ab23b04e-1d53-4ec7-b27a-e892d9298959) and [GCHandle Sample](http://msdn.microsoft.com/en-us/6acce798-0385-4ded-a790-77da842c113f).</span></span>  
  
 <span data-ttu-id="dfc46-108">Callback のサンプルで使用するアンマネージ関数とその元の関数宣言を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dfc46-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="dfc46-109">PinvokeLib.dll からエクスポートされる **TestCallBack**。</span><span class="sxs-lookup"><span data-stu-id="dfc46-109">**TestCallBack** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   <span data-ttu-id="dfc46-110">PinvokeLib.dll からエクスポートされる **TestCallBack2**。</span><span class="sxs-lookup"><span data-stu-id="dfc46-110">**TestCallBack2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 <span data-ttu-id="dfc46-111">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) はカスタム アンマネージ ライブラリであり、上で示した関数の実装を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="dfc46-111">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>  
  
 <span data-ttu-id="dfc46-112">このサンプルでは、`LibWrap` クラスには、`TestCallBack` メソッドと `TestCallBack2` メソッドのマネージ プロトタイプが含まれます。</span><span class="sxs-lookup"><span data-stu-id="dfc46-112">In this sample, the `LibWrap` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="dfc46-113">どちらのメソッドも、コールバック関数にパラメーターとしてデリゲートを渡します。</span><span class="sxs-lookup"><span data-stu-id="dfc46-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="dfc46-114">デリゲートのシグネチャは、それが参照しているメソッドのシグネチャと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dfc46-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="dfc46-115">たとえば、`FPtr` および `FPtr2` デリゲートのシグネチャは、`DoSomething` および `DoSomething2` メソッドと同じです。</span><span class="sxs-lookup"><span data-stu-id="dfc46-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="dfc46-116">プロトタイプの宣言</span><span class="sxs-lookup"><span data-stu-id="dfc46-116">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a><span data-ttu-id="dfc46-117">関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="dfc46-117">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="dfc46-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="dfc46-118">See Also</span></span>  
 [<span data-ttu-id="dfc46-119">各種のマーシャリングのサンプル</span><span class="sxs-lookup"><span data-stu-id="dfc46-119">Miscellaneous Marshaling Samples</span></span>](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)  
 [<span data-ttu-id="dfc46-120">プラットフォーム呼び出しのデータ型</span><span class="sxs-lookup"><span data-stu-id="dfc46-120">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="dfc46-121">マネージ コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="dfc46-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
