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
ms.openlocfilehash: ce5e42bb9374f22ad29ef0e97a141a796f087a98
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="98a67-102">ICorDebugChain::GetStackRange メソッド</span><span class="sxs-lookup"><span data-stu-id="98a67-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="98a67-103">このチェーンのスタック セグメントのアドレス範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="98a67-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a67-104">構文</span><span class="sxs-lookup"><span data-stu-id="98a67-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98a67-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="98a67-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="98a67-106">[out]ポインター、`CORDB_ADDRESS`は履歴のセグメントの開始アドレスを示す値。</span><span class="sxs-lookup"><span data-stu-id="98a67-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="98a67-107">[out]ポインター、`CORDB_ADDRESS`は履歴のセグメントの終了アドレスを示す値。</span><span class="sxs-lookup"><span data-stu-id="98a67-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98a67-108">コメント</span><span class="sxs-lookup"><span data-stu-id="98a67-108">Remarks</span></span>  
 <span data-ttu-id="98a67-109">数値の範囲は、スタック フレームの場所の比較に対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="98a67-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="98a67-110">実際には、スタックに格納されているデータに関するどのような想定をすることはできません。</span><span class="sxs-lookup"><span data-stu-id="98a67-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98a67-111">要件</span><span class="sxs-lookup"><span data-stu-id="98a67-111">Requirements</span></span>  
 <span data-ttu-id="98a67-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="98a67-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98a67-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98a67-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98a67-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98a67-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98a67-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98a67-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
