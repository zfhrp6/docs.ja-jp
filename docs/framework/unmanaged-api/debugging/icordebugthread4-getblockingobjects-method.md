---
title: "ICorDebugThread4::GetBlockingObjects メソッド"
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
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 006535885868ef2778146f86e5395ea1f7605d6f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="8ac14-102">ICorDebugThread4::GetBlockingObjects メソッド</span><span class="sxs-lookup"><span data-stu-id="8ac14-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="8ac14-103">順序付けされた列挙体を提供[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)構造体を提供するスレッドのブロック情報。</span><span class="sxs-lookup"><span data-stu-id="8ac14-103">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ac14-104">構文</span><span class="sxs-lookup"><span data-stu-id="8ac14-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ac14-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8ac14-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="8ac14-106">[out]順序付けされた列挙体を指すポインター [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="8ac14-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ac14-107">コメント</span><span class="sxs-lookup"><span data-stu-id="8ac14-107">Remarks</span></span>  
 <span data-ttu-id="8ac14-108">返される列挙体の最初の要素は、スレッドをブロックしている最初の構造体に対応します。</span><span class="sxs-lookup"><span data-stu-id="8ac14-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="8ac14-109">2 番目の要素がブロックされると、最初とに、非同期のプロシージャの呼び出し (APC) の実行中に検出されるブロックしている項目に対応します。</span><span class="sxs-lookup"><span data-stu-id="8ac14-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="8ac14-110">列挙体は、現在の同期状態の期間に対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="8ac14-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="8ac14-111">デバッグ対象が同期された状態では、このメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ac14-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="8ac14-112">場合`ppBlockingObjectEnum`は有効なポインターではありません、結果は未定義です。</span><span class="sxs-lookup"><span data-stu-id="8ac14-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="8ac14-113">スレッドがブロックされていて、メソッドの失敗を示す HRESULT を返します、エラーを特定することはできません。それ以外の場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="8ac14-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ac14-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="8ac14-114">Requirements</span></span>  
 <span data-ttu-id="8ac14-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8ac14-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ac14-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ac14-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ac14-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ac14-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ac14-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ac14-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac14-119">参照</span><span class="sxs-lookup"><span data-stu-id="8ac14-119">See Also</span></span>  
 [<span data-ttu-id="8ac14-120">ICorDebugThread4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8ac14-120">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="8ac14-121">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8ac14-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8ac14-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8ac14-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
