---
title: "ICorDebugChainEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChainEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3d6d587b1a249d08ffb250453fb9c007dc3df3e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="69831-102">ICorDebugChainEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="69831-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="69831-103">列挙体の現在位置から ICorDebugChain インスタンスの指定した数を取得します。</span><span class="sxs-lookup"><span data-stu-id="69831-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69831-104">構文</span><span class="sxs-lookup"><span data-stu-id="69831-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69831-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="69831-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="69831-106">[in]数`ICorDebugChain`を取得するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="69831-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="69831-107">[out]それぞれが指すポインターの配列、`ICorDebugChain`チェーンを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="69831-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="69831-108">[out]数へのポインター`ICorDebugChain`実際に返されるインスタンス。</span><span class="sxs-lookup"><span data-stu-id="69831-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="69831-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="69831-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69831-110">要件</span><span class="sxs-lookup"><span data-stu-id="69831-110">Requirements</span></span>  
 <span data-ttu-id="69831-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="69831-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69831-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69831-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69831-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69831-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69831-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69831-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
