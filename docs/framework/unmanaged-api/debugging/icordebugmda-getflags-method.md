---
title: "ICorDebugMDA::GetFlags メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugMDA.GetFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetFlags
helpviewer_keywords:
- ICorDebugMDA::GetFlags method [.NET Framework debugging]
- GetFlags method [.NET Framework debugging]
ms.assetid: 87ce7c5b-fd82-453e-bf55-c8a32150b183
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9f5a44d3bf0c689c0deb0e8c59b64124173f5645
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmdagetflags-method"></a><span data-ttu-id="377eb-102">ICorDebugMDA::GetFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="377eb-102">ICorDebugMDA::GetFlags Method</span></span>
<span data-ttu-id="377eb-103">によって表されるマネージ デバッグ アシスタント (MDA) に関連付けられているフラグを取得[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="377eb-103">Gets the flags associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="377eb-104">構文</span><span class="sxs-lookup"><span data-stu-id="377eb-104">Syntax</span></span>  
  
```  
HRESULT GetFlags (  
    [in] CorDebugMDAFlags *pFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="377eb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="377eb-105">Parameters</span></span>  
 `pFlags`  
 <span data-ttu-id="377eb-106">[in]ビットごとの組み合わせ、 [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)この MDA のフラグの設定を指定する列挙値。</span><span class="sxs-lookup"><span data-stu-id="377eb-106">[in] A bitwise combination of the [CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md) enumeration values that specify the settings of the flags for this MDA.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="377eb-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="377eb-107">Requirements</span></span>  
 <span data-ttu-id="377eb-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="377eb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="377eb-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="377eb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="377eb-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="377eb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="377eb-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="377eb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="377eb-112">参照</span><span class="sxs-lookup"><span data-stu-id="377eb-112">See Also</span></span>  
 [<span data-ttu-id="377eb-113">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="377eb-113">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="377eb-114">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="377eb-114">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
