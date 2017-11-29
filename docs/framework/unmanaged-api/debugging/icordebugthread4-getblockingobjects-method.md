---
title: "ICorDebugThread4::GetBlockingObjects メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4.GetBlockingObjects Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6783d7f9af67acdff147cc46ea4f856f9b10bf3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="fe09d-102">ICorDebugThread4::GetBlockingObjects メソッド</span><span class="sxs-lookup"><span data-stu-id="fe09d-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="fe09d-103">順序付けされた列挙体を提供[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)構造体を提供するスレッドのブロック情報。</span><span class="sxs-lookup"><span data-stu-id="fe09d-103">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe09d-104">構文</span><span class="sxs-lookup"><span data-stu-id="fe09d-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe09d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fe09d-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="fe09d-106">[out]順序付けされた列挙体を指すポインター [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="fe09d-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe09d-107">コメント</span><span class="sxs-lookup"><span data-stu-id="fe09d-107">Remarks</span></span>  
 <span data-ttu-id="fe09d-108">返される列挙体の最初の要素は、スレッドをブロックしている最初の構造体に対応します。</span><span class="sxs-lookup"><span data-stu-id="fe09d-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="fe09d-109">2 番目の要素がブロックされると、最初とに、非同期のプロシージャの呼び出し (APC) の実行中に検出されるブロックしている項目に対応します。</span><span class="sxs-lookup"><span data-stu-id="fe09d-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="fe09d-110">列挙体は、現在の同期状態の期間に対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="fe09d-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="fe09d-111">デバッグ対象が同期された状態では、このメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe09d-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="fe09d-112">場合`ppBlockingObjectEnum`は有効なポインターではありません、結果は未定義です。</span><span class="sxs-lookup"><span data-stu-id="fe09d-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="fe09d-113">スレッドがブロックされていて、メソッドの失敗を示す HRESULT を返します、エラーを特定することはできません。それ以外の場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="fe09d-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe09d-114">要件</span><span class="sxs-lookup"><span data-stu-id="fe09d-114">Requirements</span></span>  
 <span data-ttu-id="fe09d-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fe09d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe09d-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe09d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe09d-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe09d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe09d-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe09d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe09d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe09d-119">See Also</span></span>  
 [<span data-ttu-id="fe09d-120">ICorDebugThread4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe09d-120">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="fe09d-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe09d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="fe09d-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="fe09d-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
