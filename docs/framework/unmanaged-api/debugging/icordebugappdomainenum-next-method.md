---
title: "ICorDebugAppDomainEnum::Next メソッド"
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
- ICorDebugAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1c5b773cf49ed67ce6d5981650f2409f7860391a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="d890e-102">ICorDebugAppDomainEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="d890e-102">ICorDebugAppDomainEnum::Next Method</span></span>
<span data-ttu-id="d890e-103">コレクションの現在のカーソル位置から指定されたアプリケーション ドメイン数を取得します。</span><span class="sxs-lookup"><span data-stu-id="d890e-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d890e-104">構文</span><span class="sxs-lookup"><span data-stu-id="d890e-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d890e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d890e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d890e-106">[in]取得するアプリケーション ドメインの数。</span><span class="sxs-lookup"><span data-stu-id="d890e-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="d890e-107">[out]アプリケーション ドメインを表す ICorDebugAppDomain オブジェクトを指し示すそれぞれが、ポインターの配列。</span><span class="sxs-lookup"><span data-stu-id="d890e-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d890e-108">[out]実際に返されるアプリケーション ドメインの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d890e-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="d890e-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="d890e-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d890e-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="d890e-110">Requirements</span></span>  
 <span data-ttu-id="d890e-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d890e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d890e-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d890e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d890e-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d890e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d890e-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d890e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
