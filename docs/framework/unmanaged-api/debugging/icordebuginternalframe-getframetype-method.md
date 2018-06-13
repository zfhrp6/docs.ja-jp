---
title: ICorDebugInternalFrame::GetFrameType メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f7e5fceacc3fefa9267a9d7f989e745c392322e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414126"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="8c8a6-102">ICorDebugInternalFrame::GetFrameType メソッド</span><span class="sxs-lookup"><span data-stu-id="8c8a6-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="8c8a6-103">この内部フレームの型を取得します。</span><span class="sxs-lookup"><span data-stu-id="8c8a6-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c8a6-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c8a6-104">Syntax</span></span>  
  
```  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c8a6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c8a6-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="8c8a6-106">[out]これによって表される内部のフレームの型を示す CorDebugInternalFrameType 列挙型の値へのポインター`ICorDebugInternalFrame`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8c8a6-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c8a6-107">コメント</span><span class="sxs-lookup"><span data-stu-id="8c8a6-107">Remarks</span></span>  
 <span data-ttu-id="8c8a6-108">内部フレームの種類は STUBFRAME_NONE できなくなります。</span><span class="sxs-lookup"><span data-stu-id="8c8a6-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="8c8a6-109">デバッガーは正常に認識されていない内部フレームの種類を無視します。</span><span class="sxs-lookup"><span data-stu-id="8c8a6-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c8a6-110">要件</span><span class="sxs-lookup"><span data-stu-id="8c8a6-110">Requirements</span></span>  
 <span data-ttu-id="8c8a6-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8c8a6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c8a6-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c8a6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c8a6-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c8a6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c8a6-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c8a6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
