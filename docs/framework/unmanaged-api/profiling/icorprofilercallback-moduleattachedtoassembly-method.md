---
title: "ICorProfilerCallback::ModuleAttachedToAssembly メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleAttachedToAssembly
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2c285a42bb48970756a54d5313d2839c76a9835c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="48751-102">ICorProfilerCallback::ModuleAttachedToAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="48751-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="48751-103">モジュールが、親アセンブリにアタッチされていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="48751-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48751-104">構文</span><span class="sxs-lookup"><span data-stu-id="48751-104">Syntax</span></span>  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48751-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="48751-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="48751-106">[in]アタッチされるモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="48751-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="48751-107">[in]モジュールが関連付けられている親アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="48751-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48751-108">コメント</span><span class="sxs-lookup"><span data-stu-id="48751-108">Remarks</span></span>  
 <span data-ttu-id="48751-109">呼び出すことによってインポート アドレス テーブル (IAT) を通じて、モジュールを読み込むことができる`LoadLibrary`、またはメタデータの参照を使用します。</span><span class="sxs-lookup"><span data-stu-id="48751-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="48751-110">その結果、共通言語ランタイム (CLR) ローダーでは、モジュールが住んでいるアセンブリを判断するための複数のコード パスがあります。</span><span class="sxs-lookup"><span data-stu-id="48751-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="48751-111">したがって、可能であれば後に[icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)が呼び出されると、モジュールには、どのようなアセンブリはわからない内にあるし、親アセンブリ ID を取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="48751-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="48751-112">`ModuleAttachedToAssembly`モジュールが、親アセンブリとその親アセンブリの ID を取得できるに関連付けられている場合、メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="48751-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48751-113">要件</span><span class="sxs-lookup"><span data-stu-id="48751-113">Requirements</span></span>  
 <span data-ttu-id="48751-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="48751-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48751-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="48751-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="48751-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48751-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48751-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48751-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48751-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="48751-118">See Also</span></span>  
 [<span data-ttu-id="48751-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48751-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
