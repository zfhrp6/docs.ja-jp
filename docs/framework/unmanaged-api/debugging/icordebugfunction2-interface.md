---
title: ICorDebugFunction2 Interface1
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
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ac3a4cd5ec2aff1b60cd51ca33d411e5cc81eb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2-interface1"></a><span data-ttu-id="be244-102">ICorDebugFunction2 Interface1</span><span class="sxs-lookup"><span data-stu-id="be244-102">ICorDebugFunction2 Interface1</span></span>
<span data-ttu-id="be244-103">非ユーザー コードをスキップするデバッグ手順で マイ コードのみをサポートする ICorDebugFunction インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="be244-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be244-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="be244-104">Methods</span></span>  
  
|<span data-ttu-id="be244-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="be244-105">Method</span></span>|<span data-ttu-id="be244-106">説明</span><span class="sxs-lookup"><span data-stu-id="be244-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be244-107">EnumerateNativeCode メソッド</span><span class="sxs-lookup"><span data-stu-id="be244-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="be244-108">(まだ実装されていません。)ICorDebugFunction2 オブジェクトによって参照された関数のネイティブ コードのステートメントを含む ICorDebugCodeEnum へのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="be244-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="be244-109">GetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="be244-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="be244-110">この関数はユーザー コードとしてマークされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="be244-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="be244-111">GetVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="be244-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="be244-112">この関数のエディット コンティニュ バージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="be244-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="be244-113">SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="be244-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="be244-114">マイ コードのみのマークをこの関数のステップ インします。</span><span class="sxs-lookup"><span data-stu-id="be244-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be244-115">コメント</span><span class="sxs-lookup"><span data-stu-id="be244-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be244-116">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="be244-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be244-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="be244-117">Requirements</span></span>  
 <span data-ttu-id="be244-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="be244-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be244-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be244-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be244-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be244-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be244-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be244-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be244-122">参照</span><span class="sxs-lookup"><span data-stu-id="be244-122">See Also</span></span>  
 [<span data-ttu-id="be244-123">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be244-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
