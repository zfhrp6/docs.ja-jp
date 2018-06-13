---
title: ICorDebugFrame::GetFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b622d1bd82e53d5fa232e07b1f49e6fbba3ccba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414844"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="da7e6-102">ICorDebugFrame::GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="da7e6-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="da7e6-103">このスタック フレームに関連付けられているコードを含む関数を取得します。</span><span class="sxs-lookup"><span data-stu-id="da7e6-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da7e6-104">構文</span><span class="sxs-lookup"><span data-stu-id="da7e6-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da7e6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="da7e6-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="da7e6-106">[out]このスタック フレームに関連付けられているコードを含む関数を表す ICorDebugFunction オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="da7e6-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da7e6-107">コメント</span><span class="sxs-lookup"><span data-stu-id="da7e6-107">Remarks</span></span>  
 <span data-ttu-id="da7e6-108">`GetFunction`フレームは、特定の関数に関連付けられていない場合、メソッドが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="da7e6-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da7e6-109">要件</span><span class="sxs-lookup"><span data-stu-id="da7e6-109">Requirements</span></span>  
 <span data-ttu-id="da7e6-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="da7e6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da7e6-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da7e6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da7e6-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da7e6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da7e6-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da7e6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
