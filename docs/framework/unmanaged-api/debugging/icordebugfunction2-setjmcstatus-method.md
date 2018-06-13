---
title: ICorDebugFunction2::SetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15b102be5a792f982edeb320199576bdddbd859a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412361"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="78c0f-102">ICorDebugFunction2::SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="78c0f-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="78c0f-103">関数をマイ コードのみをこの ICorDebugFunction2 によって表されるマークのステップ インします。</span><span class="sxs-lookup"><span data-stu-id="78c0f-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78c0f-104">構文</span><span class="sxs-lookup"><span data-stu-id="78c0f-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78c0f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="78c0f-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="78c0f-106">[in]設定`true`ユーザー コードとして関数をマークするそれ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="78c0f-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="78c0f-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="78c0f-107">Return Values</span></span>  
  
|<span data-ttu-id="78c0f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78c0f-108">HRESULT</span></span>|<span data-ttu-id="78c0f-109">説明</span><span class="sxs-lookup"><span data-stu-id="78c0f-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="78c0f-110">関数が正常にマークされました。</span><span class="sxs-lookup"><span data-stu-id="78c0f-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="78c0f-111">デバッグできないために、関数をユーザー コードとしてマークできませんでした。</span><span class="sxs-lookup"><span data-stu-id="78c0f-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78c0f-112">コメント</span><span class="sxs-lookup"><span data-stu-id="78c0f-112">Remarks</span></span>  
 <span data-ttu-id="78c0f-113">マイ コードのみステッパは非ユーザー コードをスキップします。</span><span class="sxs-lookup"><span data-stu-id="78c0f-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="78c0f-114">ユーザー コードは、デバッグ可能なコードのサブセットである必要があります。</span><span class="sxs-lookup"><span data-stu-id="78c0f-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78c0f-115">要件</span><span class="sxs-lookup"><span data-stu-id="78c0f-115">Requirements</span></span>  
 <span data-ttu-id="78c0f-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="78c0f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78c0f-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78c0f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78c0f-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78c0f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78c0f-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78c0f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
