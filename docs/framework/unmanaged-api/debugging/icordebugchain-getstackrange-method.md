---
title: "ICorDebugChain::GetStackRange メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetStackRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37a9be7924a6d9c1f1d78bd10f9642fff22036bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="82f27-102">ICorDebugChain::GetStackRange メソッド</span><span class="sxs-lookup"><span data-stu-id="82f27-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="82f27-103">このチェーンのスタック セグメントのアドレス範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="82f27-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82f27-104">構文</span><span class="sxs-lookup"><span data-stu-id="82f27-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82f27-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82f27-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="82f27-106">[out]ポインター、`CORDB_ADDRESS`は履歴のセグメントの開始アドレスを示す値。</span><span class="sxs-lookup"><span data-stu-id="82f27-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="82f27-107">[out]ポインター、`CORDB_ADDRESS`は履歴のセグメントの終了アドレスを示す値。</span><span class="sxs-lookup"><span data-stu-id="82f27-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82f27-108">コメント</span><span class="sxs-lookup"><span data-stu-id="82f27-108">Remarks</span></span>  
 <span data-ttu-id="82f27-109">数値の範囲は、スタック フレームの場所の比較に対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="82f27-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="82f27-110">実際には、スタックに格納されているデータに関するどのような想定をすることはできません。</span><span class="sxs-lookup"><span data-stu-id="82f27-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82f27-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="82f27-111">Requirements</span></span>  
 <span data-ttu-id="82f27-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="82f27-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82f27-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82f27-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82f27-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82f27-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82f27-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82f27-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
