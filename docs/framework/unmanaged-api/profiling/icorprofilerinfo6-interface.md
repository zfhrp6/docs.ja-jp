---
title: ICorProfilerInfo6 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da1aab48e2eef229bb31e9443a5549c3f9fbc621
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455303"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="97d3c-102">ICorProfilerInfo6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="97d3c-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="97d3c-103">[.NET Framework 4.6 およびそれ以降のバージョンでサポート]</span><span class="sxs-lookup"><span data-stu-id="97d3c-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="97d3c-104">サブクラス[ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)特定 NGen モジュールおよびインラインの特定のメソッドに定義されているすべてのメソッドの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="97d3c-104">A subclass of [ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97d3c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="97d3c-105">Methods</span></span>  
  
|<span data-ttu-id="97d3c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="97d3c-106">Method</span></span>|<span data-ttu-id="97d3c-107">説明</span><span class="sxs-lookup"><span data-stu-id="97d3c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97d3c-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="97d3c-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="97d3c-109">指定した NGen モジュールに属するし、は特定のメソッドの本体でインライン展開をすべてのメソッドの列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="97d3c-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97d3c-110">要件</span><span class="sxs-lookup"><span data-stu-id="97d3c-110">Requirements</span></span>  
 <span data-ttu-id="97d3c-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="97d3c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97d3c-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="97d3c-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="97d3c-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97d3c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d3c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="97d3c-114">See Also</span></span>  
 [<span data-ttu-id="97d3c-115">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="97d3c-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
