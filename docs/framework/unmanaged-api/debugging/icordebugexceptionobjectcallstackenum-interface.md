---
title: ICorDebugExceptionObjectCallStackEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e6df9c7e24e2303571b7cb3b80ff4bf07dc59ccc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415666"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="9078e-102">ICorDebugExceptionObjectCallStackEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9078e-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="9078e-103">例外オブジェクトに埋め込まれているコール スタックの情報の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="9078e-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="9078e-104">このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="9078e-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9078e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9078e-105">Methods</span></span>  
  
|<span data-ttu-id="9078e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="9078e-106">Method</span></span>|<span data-ttu-id="9078e-107">説明</span><span class="sxs-lookup"><span data-stu-id="9078e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9078e-108">Icordebugexceptionobjectcallstackenum::next</span><span class="sxs-lookup"><span data-stu-id="9078e-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="9078e-109">指定した数を取得[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)例外オブジェクトの呼び出し履歴に関する情報を含むオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9078e-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9078e-110">コメント</span><span class="sxs-lookup"><span data-stu-id="9078e-110">Remarks</span></span>  
 <span data-ttu-id="9078e-111">`ICorDebugExceptionObjectCallStackEnum`インターフェイスは ICorDebugEnum インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="9078e-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="9078e-112">`ICorDebugExceptionObjectCallStackEnum`インスタンスが格納されます[CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)オブジェクトを呼び出して、 [icordebugexceptionobjectvalue::enumerateexceptioncallstack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9078e-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="9078e-113">呼び出して、呼び出しスタック コレクション内の項目を列挙することができます、 [icordebugexceptionobjectcallstackenum::next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)メソッド</span><span class="sxs-lookup"><span data-stu-id="9078e-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9078e-114">要件</span><span class="sxs-lookup"><span data-stu-id="9078e-114">Requirements</span></span>  
 <span data-ttu-id="9078e-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9078e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9078e-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9078e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9078e-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9078e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9078e-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9078e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9078e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9078e-119">See Also</span></span>  
 [<span data-ttu-id="9078e-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9078e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9078e-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="9078e-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
