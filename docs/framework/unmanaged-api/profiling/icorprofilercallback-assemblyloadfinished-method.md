---
title: "ICorProfilerCallback::AssemblyLoadFinished メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyLoadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: af5089603c2044b10061a32c5921b9eeadf86b36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="8656b-102">ICorProfilerCallback::AssemblyLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="8656b-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="8656b-103">アセンブリの読み込みが完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8656b-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8656b-104">構文</span><span class="sxs-lookup"><span data-stu-id="8656b-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8656b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8656b-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="8656b-106">[in]読み込まれたアセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="8656b-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="8656b-107">[in]アセンブリの読み込みが正常に終了するかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="8656b-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8656b-108">コメント</span><span class="sxs-lookup"><span data-stu-id="8656b-108">Remarks</span></span>  
 <span data-ttu-id="8656b-109">値`assemblyId`まで情報の要求に対して無効です、`AssemblyLoadFinished`メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8656b-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="8656b-110">アセンブリの読み込みの一部が後に続ける可能性があります、`AssemblyLoadFinished`コールバック。</span><span class="sxs-lookup"><span data-stu-id="8656b-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="8656b-111">失敗を示す HRESULT で`hrStatus`は失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="8656b-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="8656b-112">ただし、成功 HRESULT で`hrStatus`のみのアセンブリの読み込みの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="8656b-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8656b-113">要件</span><span class="sxs-lookup"><span data-stu-id="8656b-113">Requirements</span></span>  
 <span data-ttu-id="8656b-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8656b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8656b-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8656b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8656b-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8656b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8656b-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8656b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8656b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8656b-118">See Also</span></span>  
 [<span data-ttu-id="8656b-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8656b-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
