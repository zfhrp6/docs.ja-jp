---
title: "ICorProfilerInfo6 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 805f1e451b2c13c356d904c42dff87304aa2093c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="3a461-102">ICorProfilerInfo6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a461-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="3a461-103">[.NET Framework 4.6 およびそれ以降のバージョンでサポート]</span><span class="sxs-lookup"><span data-stu-id="3a461-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="3a461-104">サブクラス[ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)特定 NGen モジュールおよびインラインの特定のメソッドに定義されているすべてのメソッドの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="3a461-104">A subclass of [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a461-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3a461-105">Methods</span></span>  
  
|<span data-ttu-id="3a461-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="3a461-106">Method</span></span>|<span data-ttu-id="3a461-107">説明</span><span class="sxs-lookup"><span data-stu-id="3a461-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a461-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="3a461-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="3a461-109">指定した NGen モジュールに属するし、は特定のメソッドの本体でインライン展開をすべてのメソッドの列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="3a461-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a461-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="3a461-110">Requirements</span></span>  
 <span data-ttu-id="3a461-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3a461-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a461-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3a461-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3a461-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a461-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a461-114">参照</span><span class="sxs-lookup"><span data-stu-id="3a461-114">See Also</span></span>  
 [<span data-ttu-id="3a461-115">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a461-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
