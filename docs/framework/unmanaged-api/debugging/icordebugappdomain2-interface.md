---
title: ICorDebugAppDomain2 Interface1
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
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c811107fcf32696aee17810af06ac0b2ddc9102d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain2-interface1"></a><span data-ttu-id="985ec-102">ICorDebugAppDomain2 Interface1</span><span class="sxs-lookup"><span data-stu-id="985ec-102">ICorDebugAppDomain2 Interface1</span></span>
<span data-ttu-id="985ec-103">配列、ポインター、関数ポインター、および参照型を使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="985ec-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="985ec-104">このインターフェイスは、ICorDebugAppDomain インターフェイスの拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="985ec-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="985ec-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="985ec-105">Methods</span></span>  
  
|<span data-ttu-id="985ec-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="985ec-106">Method</span></span>|<span data-ttu-id="985ec-107">説明</span><span class="sxs-lookup"><span data-stu-id="985ec-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="985ec-108">GetArrayOrPointerType メソッド</span><span class="sxs-lookup"><span data-stu-id="985ec-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="985ec-109">指定された型、ポインター、または指定した型への参照の配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="985ec-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="985ec-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="985ec-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="985ec-111">指定したシグネチャを持つ関数へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="985ec-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="985ec-112">コメント</span><span class="sxs-lookup"><span data-stu-id="985ec-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="985ec-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="985ec-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="985ec-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="985ec-114">Requirements</span></span>  
 <span data-ttu-id="985ec-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="985ec-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="985ec-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="985ec-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="985ec-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="985ec-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="985ec-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="985ec-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="985ec-119">参照</span><span class="sxs-lookup"><span data-stu-id="985ec-119">See Also</span></span>  
 [<span data-ttu-id="985ec-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="985ec-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
