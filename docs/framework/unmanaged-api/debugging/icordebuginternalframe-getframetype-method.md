---
title: "ICorDebugInternalFrame::GetFrameType メソッド"
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
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 476903ae8f1461a46d685bc3e549c3b6553d5c68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="f602d-102">ICorDebugInternalFrame::GetFrameType メソッド</span><span class="sxs-lookup"><span data-stu-id="f602d-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="f602d-103">この内部フレームの型を取得します。</span><span class="sxs-lookup"><span data-stu-id="f602d-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f602d-104">構文</span><span class="sxs-lookup"><span data-stu-id="f602d-104">Syntax</span></span>  
  
```  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f602d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f602d-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="f602d-106">[out]これによって表される内部のフレームの型を示す CorDebugInternalFrameType 列挙型の値へのポインター`ICorDebugInternalFrame`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f602d-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f602d-107">コメント</span><span class="sxs-lookup"><span data-stu-id="f602d-107">Remarks</span></span>  
 <span data-ttu-id="f602d-108">内部フレームの種類は STUBFRAME_NONE できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f602d-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="f602d-109">デバッガーは正常に認識されていない内部フレームの種類を無視します。</span><span class="sxs-lookup"><span data-stu-id="f602d-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f602d-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="f602d-110">Requirements</span></span>  
 <span data-ttu-id="f602d-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f602d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f602d-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f602d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f602d-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f602d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f602d-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f602d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
