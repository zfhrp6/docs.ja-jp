---
title: "ICorDebugManagedCallback::Break メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.Break
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ce51ed25ecd5570ce3c5d9acc1ec3750b289f095
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="6685d-102">ICorDebugManagedCallback::Break メソッド</span><span class="sxs-lookup"><span data-stu-id="6685d-102">ICorDebugManagedCallback::Break Method</span></span>
<span data-ttu-id="6685d-103">デバッガーに通知時に、<xref:System.Reflection.Emit.OpCodes.Break>コード ストリーム内の命令を実行します。</span><span class="sxs-lookup"><span data-stu-id="6685d-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6685d-104">構文</span><span class="sxs-lookup"><span data-stu-id="6685d-104">Syntax</span></span>  
  
```  
HRESULT Break (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6685d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6685d-105">Parameters</span></span>  
 `pAppDOmain`  
 <span data-ttu-id="6685d-106">[in]Break 命令が含まれるアプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6685d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>  
  
 `thread`  
 <span data-ttu-id="6685d-107">[in]Break 命令が含まれる、スレッドを表す ICorDebugThread オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6685d-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6685d-108">要件</span><span class="sxs-lookup"><span data-stu-id="6685d-108">Requirements</span></span>  
 <span data-ttu-id="6685d-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6685d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6685d-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6685d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6685d-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6685d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6685d-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6685d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6685d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="6685d-113">See Also</span></span>  
 [<span data-ttu-id="6685d-114">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6685d-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
