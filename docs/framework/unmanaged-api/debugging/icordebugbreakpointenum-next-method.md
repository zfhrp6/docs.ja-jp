---
title: "ICorDebugBreakpointEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBreakpointEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBreakpointEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBreakpointEnum interface [.NET Framework debugging]
- ICorDebugBreakpointEnum::Next method [.NET Framework debugging]
ms.assetid: 2e6bbaea-79ba-448c-a0e3-7c90fc7c2939
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b81da25a630b034d4ec2f277f738a5337bdbec3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugbreakpointenumnext-method"></a><span data-ttu-id="6aac5-102">ICorDebugBreakpointEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="6aac5-102">ICorDebugBreakpointEnum::Next Method</span></span>
<span data-ttu-id="6aac5-103">列挙体の現在位置から ICorDebugBreakpoint インスタンスの指定した数を取得します。</span><span class="sxs-lookup"><span data-stu-id="6aac5-103">Gets the specified number of ICorDebugBreakpoint instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aac5-104">構文</span><span class="sxs-lookup"><span data-stu-id="6aac5-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6aac5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6aac5-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6aac5-106">[in]数`ICorDebugBreakpoint`を取得するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="6aac5-106">[in] The number of `ICorDebugBreakpoint` instances to be retrieved.</span></span>  
  
 `breakpoints`  
 <span data-ttu-id="6aac5-107">[out]それぞれが指すポインターの配列、`ICorDebugBreakpoint`ブレークポイントを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6aac5-107">[out] An array of pointers, each of which points to an `ICorDebugBreakpoint` object that represents a breakpoint.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6aac5-108">[out]数へのポインター`ICorDebugBreakpoint`実際に返されるインスタンス。</span><span class="sxs-lookup"><span data-stu-id="6aac5-108">[out] A pointer to the number of `ICorDebugBreakpoint` instances actually returned.</span></span> <span data-ttu-id="6aac5-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="6aac5-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aac5-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="6aac5-110">Requirements</span></span>  
 <span data-ttu-id="6aac5-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6aac5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aac5-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6aac5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6aac5-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6aac5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6aac5-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aac5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
