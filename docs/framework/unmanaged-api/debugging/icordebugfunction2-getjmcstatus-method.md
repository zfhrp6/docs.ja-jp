---
title: ICorDebugFunction2::GetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acf0ba3938568524479e12b93ae8cebbcf52f909
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411730"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="0b33e-102">ICorDebugFunction2::GetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="0b33e-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="0b33e-103">ICorDebugFunction2 オブジェクトによって表される関数がユーザー コードとしてマークされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="0b33e-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b33e-104">構文</span><span class="sxs-lookup"><span data-stu-id="0b33e-104">Syntax</span></span>  
  
```  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b33e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0b33e-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="0b33e-106">[out]ブール値へのポインター`true`場合は、この関数がユーザー コードとしてマークされている以外の値は、それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="0b33e-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b33e-107">コメント</span><span class="sxs-lookup"><span data-stu-id="0b33e-107">Remarks</span></span>  
 <span data-ttu-id="0b33e-108">場合は、関数は、これによって表される`ICorDebugFunction2`デバッグできません`pbIsJustMyCode`が必ず`false`です。</span><span class="sxs-lookup"><span data-stu-id="0b33e-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b33e-109">要件</span><span class="sxs-lookup"><span data-stu-id="0b33e-109">Requirements</span></span>  
 <span data-ttu-id="0b33e-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0b33e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b33e-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b33e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b33e-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b33e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b33e-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b33e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
