---
title: "ICorProfilerCallback::Shutdown メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.Shutdown
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42c9abc3c255f7ddda5e7934c495b073a7b1f6fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="f4ac3-102">ICorProfilerCallback::Shutdown メソッド</span><span class="sxs-lookup"><span data-stu-id="f4ac3-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="f4ac3-103">アプリケーションがシャット ダウンしているプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="f4ac3-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4ac3-104">構文</span><span class="sxs-lookup"><span data-stu-id="f4ac3-104">Syntax</span></span>  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f4ac3-105">コメント</span><span class="sxs-lookup"><span data-stu-id="f4ac3-105">Remarks</span></span>  
 <span data-ttu-id="f4ac3-106">プロファイラー コードがのメソッドを安全に呼び出すことはできません、 [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)インターフェイスの後に、`Shutdown`メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f4ac3-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="f4ac3-107">呼び出しの`ICorProfilerInfo`メソッドの後に未定義の動作が発生、`Shutdown`メソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="f4ac3-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="f4ac3-108">シャット ダウン後にこの特定の変更できないイベントがあります。プロファイラーは、これが発生するとすぐに戻ります注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4ac3-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="f4ac3-109">`Shutdown`プロファイリングされているマネージ アプリケーションがマネージ コードとして開始された場合のみ、メソッドが呼び出されます (つまり、プロセスのスタックの初期のフレームが管理対象)。</span><span class="sxs-lookup"><span data-stu-id="f4ac3-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="f4ac3-110">アプリケーションがアンマネージ コードとして開始された後でマネージ コードにジャンプする場合は、それによってインスタンスを作成する共通言語ランタイム (CLR) の`Shutdown`は呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="f4ac3-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="f4ac3-111">このような場合、プロファイラーが、ライブラリに含める必要があります、`DllMain`ルーチン、ありますを使用する値の任意のリソースを解放し、トレースなどのディスクにフラッシュなど、そのデータのクリーンアップ処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="f4ac3-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="f4ac3-112">一般に、プロファイラーは、予期しないシャット ダウンに対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4ac3-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="f4ac3-113">たとえば、win32 のプロセスを中止する可能性があります`TerminateProcess`メソッド (Winbase.h で宣言)。</span><span class="sxs-lookup"><span data-stu-id="f4ac3-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="f4ac3-114">それ以外の場合、CLR は、それらの計画的な破壊メッセージを配信せず特定のマネージ スレッド (バック グラウンド スレッド) を停止します。</span><span class="sxs-lookup"><span data-stu-id="f4ac3-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4ac3-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="f4ac3-115">Requirements</span></span>  
 <span data-ttu-id="f4ac3-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f4ac3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4ac3-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f4ac3-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f4ac3-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4ac3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4ac3-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4ac3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ac3-120">参照</span><span class="sxs-lookup"><span data-stu-id="f4ac3-120">See Also</span></span>  
 [<span data-ttu-id="f4ac3-121">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4ac3-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="f4ac3-122">Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="f4ac3-122">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
