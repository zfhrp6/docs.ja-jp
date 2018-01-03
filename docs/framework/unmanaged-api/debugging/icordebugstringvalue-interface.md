---
title: ICorDebugStringValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStringValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStringValue
helpviewer_keywords: ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9958e6f5ad73658b278d83c78e58cf4166d5642
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstringvalue-interface1"></a><span data-ttu-id="81c21-102">ICorDebugStringValue Interface1</span><span class="sxs-lookup"><span data-stu-id="81c21-102">ICorDebugStringValue Interface1</span></span>
<span data-ttu-id="81c21-103">文字列の値に適用される ICorDebugHeapValue のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="81c21-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="81c21-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="81c21-104">Methods</span></span>  
  
|<span data-ttu-id="81c21-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="81c21-105">Method</span></span>|<span data-ttu-id="81c21-106">説明</span><span class="sxs-lookup"><span data-stu-id="81c21-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="81c21-107">GetLength メソッド</span><span class="sxs-lookup"><span data-stu-id="81c21-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="81c21-108">これによって参照される文字列の文字数を取得`ICorDebugStringValue`です。</span><span class="sxs-lookup"><span data-stu-id="81c21-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="81c21-109">GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="81c21-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="81c21-110">これによって参照される文字列を取得`ICorDebugStringValue`です。</span><span class="sxs-lookup"><span data-stu-id="81c21-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81c21-111">コメント</span><span class="sxs-lookup"><span data-stu-id="81c21-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81c21-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="81c21-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81c21-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="81c21-113">Requirements</span></span>  
 <span data-ttu-id="81c21-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="81c21-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81c21-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81c21-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81c21-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81c21-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81c21-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81c21-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81c21-118">参照</span><span class="sxs-lookup"><span data-stu-id="81c21-118">See Also</span></span>  
 [<span data-ttu-id="81c21-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81c21-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
