---
title: "ICorDebugILFrame::CanSetIP メソッド"
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
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 22d0df9add0a4ce35b1a590d65e30a6756fec49c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="1cd2a-102">ICorDebugILFrame::CanSetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="1cd2a-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="1cd2a-103">Microsoft Intermediate Language (MSIL) コードで指定されたオフセット位置に、命令ポインターを設定しても安全かどうかを示す HRESULT を取得します。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cd2a-104">構文</span><span class="sxs-lookup"><span data-stu-id="1cd2a-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cd2a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1cd2a-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="1cd2a-106">[in]命令ポインターの必要な設定です。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cd2a-107">コメント</span><span class="sxs-lookup"><span data-stu-id="1cd2a-107">Remarks</span></span>  
 <span data-ttu-id="1cd2a-108">使用して、`CanSetIP`メソッドを呼び出す前に、 [icordebugilframe::setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="1cd2a-109">場合`CanSetIP`HRESULT を返します、S_OK 以外を呼び出すことができますも`ICorDebugILFrame::SetIP`デバッガーがデバッグ中のコードの安全で適切な実行を続けることという保証はありません。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cd2a-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="1cd2a-110">Requirements</span></span>  
 <span data-ttu-id="1cd2a-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1cd2a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cd2a-112">**ヘッダー:** CorDebug.idl、CorDebug、h</span><span class="sxs-lookup"><span data-stu-id="1cd2a-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="1cd2a-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cd2a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cd2a-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cd2a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
