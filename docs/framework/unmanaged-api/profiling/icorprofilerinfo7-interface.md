---
title: "ICorProfilerInfo7 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13282bec74df5e6159148aa4fbe92a84d035e044
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="a4ced-102">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4ced-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="a4ced-103">[[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] 以降のバージョンでサポート]</span><span class="sxs-lookup"><span data-stu-id="a4ced-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="a4ced-104">サブクラス[ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)新しくを適用するためのメソッドでは、モジュールにメタデータが定義されているし、メモリ内のシンボルのストリームへのアクセスを提供するを提供します。</span><span class="sxs-lookup"><span data-stu-id="a4ced-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a4ced-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a4ced-105">Methods</span></span>  
  
|<span data-ttu-id="a4ced-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a4ced-106">Method</span></span>|<span data-ttu-id="a4ced-107">説明</span><span class="sxs-lookup"><span data-stu-id="a4ced-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4ced-108">ApplyMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="a4ced-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="a4ced-109">新しく定義されたメタデータを適用、`IMetadataEmit::Define*`メソッドを指定されたモジュール。</span><span class="sxs-lookup"><span data-stu-id="a4ced-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="a4ced-110">GetInMemorySymbolsLength メソッド</span><span class="sxs-lookup"><span data-stu-id="a4ced-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="a4ced-111">メモリ内のシンボルのストリームの長さを返します。</span><span class="sxs-lookup"><span data-stu-id="a4ced-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="a4ced-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="a4ced-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="a4ced-113">メモリ内のシンボルのストリームからバイトを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="a4ced-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a4ced-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="a4ced-114">Requirements</span></span>  
 <span data-ttu-id="a4ced-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a4ced-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4ced-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a4ced-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a4ced-117">**.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4ced-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ced-118">参照</span><span class="sxs-lookup"><span data-stu-id="a4ced-118">See Also</span></span>  
 [<span data-ttu-id="a4ced-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4ced-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
