---
title: "ICorProfilerCallback::ExceptionCLRCatcherFound メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCLRCatcherFound
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ebb1779ca9f09089a071673f92810ea7a9e76b3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="dcf0f-102">ICorProfilerCallback::ExceptionCLRCatcherFound メソッド</span><span class="sxs-lookup"><span data-stu-id="dcf0f-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="dcf0f-103">ときに呼び出されます、`catch`ブロックは、共通言語ランタイム (CLR) 自体の内部例外を検出します。</span><span class="sxs-lookup"><span data-stu-id="dcf0f-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="dcf0f-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="dcf0f-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcf0f-105">構文</span><span class="sxs-lookup"><span data-stu-id="dcf0f-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="dcf0f-106">要件</span><span class="sxs-lookup"><span data-stu-id="dcf0f-106">Requirements</span></span>  
 <span data-ttu-id="dcf0f-107">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dcf0f-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcf0f-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dcf0f-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dcf0f-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcf0f-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcf0f-110">**.NET framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="dcf0f-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcf0f-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcf0f-111">See Also</span></span>  
 [<span data-ttu-id="dcf0f-112">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dcf0f-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="dcf0f-113">ExceptionCLRCatcherExecute メソッド</span><span class="sxs-lookup"><span data-stu-id="dcf0f-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
