---
title: ICorDebugComObjectValue のインターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11afee9c2a84999ccad2cdc12e2a14a4dc17d542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412522"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="e860a-102">ICorDebugComObjectValue のインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e860a-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="e860a-103">ランタイム呼び出し可能ラッパー (RCW) に関連付けられている情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e860a-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e860a-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="e860a-104">Methods</span></span>  
  
|<span data-ttu-id="e860a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e860a-105">Method</span></span>|<span data-ttu-id="e860a-106">説明</span><span class="sxs-lookup"><span data-stu-id="e860a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e860a-107">GetCachedInterfacePointers メソッド</span><span class="sxs-lookup"><span data-stu-id="e860a-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="e860a-108">現在、RCW でキャッシュされた生のインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="e860a-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="e860a-109">GetCachedInterfaceTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="e860a-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="e860a-110">現在のオブジェクトを大文字と小文字またはとして使用されることは、インターフェイスの種類の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="e860a-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e860a-111">コメント</span><span class="sxs-lookup"><span data-stu-id="e860a-111">Remarks</span></span>  
 <span data-ttu-id="e860a-112">デバッガーには、"ICorDebugValue"インターフェイスのインスタンスが、RCW を表すかどうかを確認する`QueryInterface`上で"ICorDebugValue"`IID_ICorDebugComObjectValue`です。</span><span class="sxs-lookup"><span data-stu-id="e860a-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e860a-113">要件</span><span class="sxs-lookup"><span data-stu-id="e860a-113">Requirements</span></span>  
 <span data-ttu-id="e860a-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e860a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e860a-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e860a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e860a-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e860a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e860a-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e860a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e860a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e860a-118">See Also</span></span>  
 [<span data-ttu-id="e860a-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e860a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e860a-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="e860a-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
