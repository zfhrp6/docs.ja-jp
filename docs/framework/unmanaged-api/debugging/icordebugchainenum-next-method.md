---
title: ICorDebugChainEnum::Next メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd4f27b958aa4b25c2662d8a5e9da6bcdc73d5d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404457"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="a645e-102">ICorDebugChainEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="a645e-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="a645e-103">列挙体の現在位置から ICorDebugChain インスタンスの指定した数を取得します。</span><span class="sxs-lookup"><span data-stu-id="a645e-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a645e-104">構文</span><span class="sxs-lookup"><span data-stu-id="a645e-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a645e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a645e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a645e-106">[in]数`ICorDebugChain`を取得するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="a645e-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="a645e-107">[out]それぞれが指すポインターの配列、`ICorDebugChain`チェーンを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a645e-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a645e-108">[out]数へのポインター`ICorDebugChain`実際に返されるインスタンス。</span><span class="sxs-lookup"><span data-stu-id="a645e-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="a645e-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="a645e-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a645e-110">要件</span><span class="sxs-lookup"><span data-stu-id="a645e-110">Requirements</span></span>  
 <span data-ttu-id="a645e-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a645e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a645e-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a645e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a645e-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a645e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a645e-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a645e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
