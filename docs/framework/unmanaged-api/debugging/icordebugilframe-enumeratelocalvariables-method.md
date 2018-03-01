---
title: "ICorDebugILFrame::EnumerateLocalVariables メソッド"
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
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3a1b53dbefefcea6003ec4a61c8169ed96bac701
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="dd135-102">ICorDebugILFrame::EnumerateLocalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="dd135-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="dd135-103">このフレームのローカル変数の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="dd135-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd135-104">構文</span><span class="sxs-lookup"><span data-stu-id="dd135-104">Syntax</span></span>  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd135-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dd135-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="dd135-106">[out]このフレームのローカル変数の列挙子である ICorDebugValueEnum オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dd135-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd135-107">コメント</span><span class="sxs-lookup"><span data-stu-id="dd135-107">Remarks</span></span>  
 <span data-ttu-id="dd135-108">`EnumerateLocalVariables`ICorDebugILFrame オブジェクトによって表される呼び出しフレームで使用できるローカル変数の一覧を表示する列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="dd135-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="dd135-109">一覧が含まれない場合ローカル変数の実行中の関数では、アクティブなそれらの一部はない可能性がします。</span><span class="sxs-lookup"><span data-stu-id="dd135-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd135-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="dd135-110">Requirements</span></span>  
 <span data-ttu-id="dd135-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd135-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd135-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd135-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd135-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd135-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd135-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd135-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
