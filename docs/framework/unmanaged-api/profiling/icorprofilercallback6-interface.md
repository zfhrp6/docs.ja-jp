---
title: "ICorProfilerCallback6 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dca83aca3aee4a072e90793e1bb33526b6e5ebd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="79232-102">ICorProfilerCallback6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79232-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="79232-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="79232-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="79232-104">サブクラス[ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)共通言語ランタイムを使用してアセンブリを読み込んでいるプロファイラーに通知するコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="79232-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79232-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="79232-105">Methods</span></span>  
  
|<span data-ttu-id="79232-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="79232-106">Method</span></span>|<span data-ttu-id="79232-107">説明</span><span class="sxs-lookup"><span data-stu-id="79232-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79232-108">GetAssemblyReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="79232-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="79232-109">共通言語ランタイムがアセンブリ参照クロージャのウォークを実行するときに、アセンブリがごく初期のローディング状態であることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="79232-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79232-110">コメント</span><span class="sxs-lookup"><span data-stu-id="79232-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79232-111">要件</span><span class="sxs-lookup"><span data-stu-id="79232-111">Requirements</span></span>  
 <span data-ttu-id="79232-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="79232-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79232-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="79232-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79232-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79232-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79232-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="79232-115">See Also</span></span>  
 [<span data-ttu-id="79232-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="79232-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
