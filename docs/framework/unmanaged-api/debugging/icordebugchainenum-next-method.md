---
title: "ICorDebugChainEnum::Next メソッド"
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
- ICorDebugChainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e78340d26e4a7ab67fa6c312b1dbd537c5c0a28c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="f8aa1-102">ICorDebugChainEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="f8aa1-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="f8aa1-103">列挙体の現在位置から ICorDebugChain インスタンスの指定した数を取得します。</span><span class="sxs-lookup"><span data-stu-id="f8aa1-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8aa1-104">構文</span><span class="sxs-lookup"><span data-stu-id="f8aa1-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8aa1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f8aa1-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f8aa1-106">[in]数`ICorDebugChain`を取得するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="f8aa1-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="f8aa1-107">[out]それぞれが指すポインターの配列、`ICorDebugChain`チェーンを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f8aa1-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f8aa1-108">[out]数へのポインター`ICorDebugChain`実際に返されるインスタンス。</span><span class="sxs-lookup"><span data-stu-id="f8aa1-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="f8aa1-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="f8aa1-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8aa1-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="f8aa1-110">Requirements</span></span>  
 <span data-ttu-id="f8aa1-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f8aa1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8aa1-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8aa1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8aa1-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8aa1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8aa1-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8aa1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
