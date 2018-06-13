---
title: ICorDebugChain::GetStackRange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 226f8c431b90d53366aa5e504101e7de581ec570
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402471"
---
# <a name="icordebugchaingetstackrange-method"></a><span data-ttu-id="543cd-102">ICorDebugChain::GetStackRange メソッド</span><span class="sxs-lookup"><span data-stu-id="543cd-102">ICorDebugChain::GetStackRange Method</span></span>
<span data-ttu-id="543cd-103">このチェーンのスタック セグメントのアドレス範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="543cd-103">Gets the address range of the stack segment for this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="543cd-104">構文</span><span class="sxs-lookup"><span data-stu-id="543cd-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="543cd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="543cd-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="543cd-106">[out]ポインター、`CORDB_ADDRESS`は履歴のセグメントの開始アドレスを示す値。</span><span class="sxs-lookup"><span data-stu-id="543cd-106">[out] A pointer to a `CORDB_ADDRESS` value that is the starting address of the stack segment.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="543cd-107">[out]ポインター、`CORDB_ADDRESS`は履歴のセグメントの終了アドレスを示す値。</span><span class="sxs-lookup"><span data-stu-id="543cd-107">[out] A pointer to a `CORDB_ADDRESS` value that is the ending address of the stack segment.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="543cd-108">コメント</span><span class="sxs-lookup"><span data-stu-id="543cd-108">Remarks</span></span>  
 <span data-ttu-id="543cd-109">数値の範囲は、スタック フレームの場所の比較に対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="543cd-109">The numeric range is meaningful only for comparison of stack frame locations.</span></span> <span data-ttu-id="543cd-110">実際には、スタックに格納されているデータに関するどのような想定をすることはできません。</span><span class="sxs-lookup"><span data-stu-id="543cd-110">You cannot make any assumptions about what is actually stored on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="543cd-111">要件</span><span class="sxs-lookup"><span data-stu-id="543cd-111">Requirements</span></span>  
 <span data-ttu-id="543cd-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="543cd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="543cd-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="543cd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="543cd-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="543cd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="543cd-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="543cd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
