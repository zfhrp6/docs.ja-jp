---
title: "ICorDebugRegisterSet::SetThreadContext メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.SetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9a97706e5cf407f16b6d06efce11576fbb131d1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="7cbe5-102">ICorDebugRegisterSet::SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="7cbe5-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="7cbe5-103">`SetThreadContext`.NET Framework version 2.0 では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="7cbe5-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="7cbe5-104">このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="7cbe5-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cbe5-105">上位レベルの操作を使用して[icordebugnativeframe::setip](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)スレッドのコンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="7cbe5-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cbe5-106">構文</span><span class="sxs-lookup"><span data-stu-id="7cbe5-106">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="7cbe5-107">要件</span><span class="sxs-lookup"><span data-stu-id="7cbe5-107">Requirements</span></span>  
 <span data-ttu-id="7cbe5-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7cbe5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cbe5-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cbe5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cbe5-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cbe5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cbe5-111">**.NET framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="7cbe5-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cbe5-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7cbe5-112">See Also</span></span>  
 [<span data-ttu-id="7cbe5-113">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7cbe5-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="7cbe5-114">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7cbe5-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
