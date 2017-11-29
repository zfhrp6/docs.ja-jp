---
title: "ICorDebugFunction2::SetJMCStatus メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ecbcd5b8171a169fbfdd7175d3d9dfbbcb3855f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="e29ee-102">ICorDebugFunction2::SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="e29ee-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="e29ee-103">関数をマイ コードのみをこの ICorDebugFunction2 によって表されるマークのステップ インします。</span><span class="sxs-lookup"><span data-stu-id="e29ee-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e29ee-104">構文</span><span class="sxs-lookup"><span data-stu-id="e29ee-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e29ee-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e29ee-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="e29ee-106">[in]設定`true`ユーザー コードとして関数をマークするそれ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="e29ee-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="e29ee-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="e29ee-107">Return Values</span></span>  
  
|<span data-ttu-id="e29ee-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e29ee-108">HRESULT</span></span>|<span data-ttu-id="e29ee-109">説明</span><span class="sxs-lookup"><span data-stu-id="e29ee-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e29ee-110">関数が正常にマークされました。</span><span class="sxs-lookup"><span data-stu-id="e29ee-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="e29ee-111">デバッグできないために、関数をユーザー コードとしてマークできませんでした。</span><span class="sxs-lookup"><span data-stu-id="e29ee-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e29ee-112">コメント</span><span class="sxs-lookup"><span data-stu-id="e29ee-112">Remarks</span></span>  
 <span data-ttu-id="e29ee-113">マイ コードのみステッパは非ユーザー コードをスキップします。</span><span class="sxs-lookup"><span data-stu-id="e29ee-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="e29ee-114">ユーザー コードは、デバッグ可能なコードのサブセットである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e29ee-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e29ee-115">要件</span><span class="sxs-lookup"><span data-stu-id="e29ee-115">Requirements</span></span>  
 <span data-ttu-id="e29ee-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e29ee-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e29ee-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e29ee-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e29ee-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e29ee-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e29ee-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e29ee-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
