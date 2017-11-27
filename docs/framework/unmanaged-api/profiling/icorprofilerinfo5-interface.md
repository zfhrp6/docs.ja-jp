---
title: "ICorProfilerInfo5 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo5
api_location: mscorwks.dll
api_type: COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 84744474b9eca96cae5e96b8c4eadc4109f85f82
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="18ea3-102">ICorProfilerInfo5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="18ea3-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="18ea3-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="18ea3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="18ea3-104">サブクラス[ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)共通言語ランタイム (CLR) のイベントの監視の制御に通信するためにコード プロファイラーで使用するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="18ea3-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="18ea3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="18ea3-105">Methods</span></span>  
  
|<span data-ttu-id="18ea3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="18ea3-106">Method</span></span>|<span data-ttu-id="18ea3-107">説明</span><span class="sxs-lookup"><span data-stu-id="18ea3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="18ea3-108">GetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="18ea3-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="18ea3-109">プロファイラーが CLR からの通知を受信するための現在のイベント カテゴリーを取得します。</span><span class="sxs-lookup"><span data-stu-id="18ea3-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="18ea3-110">SetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="18ea3-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="18ea3-111">プロファイラーが CLR からのイベント通知を受信するためのイベントの種類を指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="18ea3-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18ea3-112">コメント</span><span class="sxs-lookup"><span data-stu-id="18ea3-112">Remarks</span></span>  
 <span data-ttu-id="18ea3-113">このインターフェイスで使用可能なメソッドを置き換えるものでは、 [icorprofilerinfo::geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)と[icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="18ea3-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18ea3-114">要件</span><span class="sxs-lookup"><span data-stu-id="18ea3-114">Requirements</span></span>  
 <span data-ttu-id="18ea3-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="18ea3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18ea3-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="18ea3-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="18ea3-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18ea3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18ea3-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="18ea3-118">See Also</span></span>  
 [<span data-ttu-id="18ea3-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="18ea3-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
