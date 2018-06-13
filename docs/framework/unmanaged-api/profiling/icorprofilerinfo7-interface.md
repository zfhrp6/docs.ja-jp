---
title: ICorProfilerInfo7 インターフェイス
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79a722cd3318def36c20a49c1567c6f0d4989d39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455407"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="ee692-102">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee692-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="ee692-103">[[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] 以降のバージョンでサポート]</span><span class="sxs-lookup"><span data-stu-id="ee692-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="ee692-104">サブクラス[ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)新しくを適用するためのメソッドでは、モジュールにメタデータが定義されているし、メモリ内のシンボルのストリームへのアクセスを提供するを提供します。</span><span class="sxs-lookup"><span data-stu-id="ee692-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee692-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ee692-105">Methods</span></span>  
  
|<span data-ttu-id="ee692-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="ee692-106">Method</span></span>|<span data-ttu-id="ee692-107">説明</span><span class="sxs-lookup"><span data-stu-id="ee692-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee692-108">ApplyMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="ee692-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="ee692-109">新しく定義されたメタデータを適用、`IMetadataEmit::Define*`メソッドを指定されたモジュール。</span><span class="sxs-lookup"><span data-stu-id="ee692-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="ee692-110">GetInMemorySymbolsLength メソッド</span><span class="sxs-lookup"><span data-stu-id="ee692-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="ee692-111">メモリ内のシンボルのストリームの長さを返します。</span><span class="sxs-lookup"><span data-stu-id="ee692-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="ee692-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="ee692-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="ee692-113">メモリ内のシンボルのストリームからバイトを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="ee692-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee692-114">要件</span><span class="sxs-lookup"><span data-stu-id="ee692-114">Requirements</span></span>  
 <span data-ttu-id="ee692-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ee692-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee692-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ee692-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ee692-117">**.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee692-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee692-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee692-118">See Also</span></span>  
 [<span data-ttu-id="ee692-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee692-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
