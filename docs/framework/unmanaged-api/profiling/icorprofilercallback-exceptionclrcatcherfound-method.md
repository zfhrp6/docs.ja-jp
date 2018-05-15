---
title: ICorProfilerCallback::ExceptionCLRCatcherFound メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33dc6a863af0c03066d5f01e5101c9a6cc6d5859
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="f124a-102">ICorProfilerCallback::ExceptionCLRCatcherFound メソッド</span><span class="sxs-lookup"><span data-stu-id="f124a-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="f124a-103">ときに呼び出されます、`catch`ブロックは、共通言語ランタイム (CLR) 自体の内部例外を検出します。</span><span class="sxs-lookup"><span data-stu-id="f124a-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="f124a-104">このメソッドは、.NET Framework version 2.0 廃止されています。</span><span class="sxs-lookup"><span data-stu-id="f124a-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f124a-105">構文</span><span class="sxs-lookup"><span data-stu-id="f124a-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f124a-106">要件</span><span class="sxs-lookup"><span data-stu-id="f124a-106">Requirements</span></span>  
 <span data-ttu-id="f124a-107">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f124a-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f124a-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f124a-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f124a-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f124a-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f124a-110">**.NET framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="f124a-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f124a-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="f124a-111">See Also</span></span>  
 [<span data-ttu-id="f124a-112">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f124a-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="f124a-113">ExceptionCLRCatcherExecute メソッド</span><span class="sxs-lookup"><span data-stu-id="f124a-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
