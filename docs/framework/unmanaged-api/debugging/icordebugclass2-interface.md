---
title: ICorDebugClass2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass2
helpviewer_keywords: ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9c4f96f084a96ccdc9857a64217284b485aa73a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugclass2-interface1"></a><span data-ttu-id="4aa43-102">ICorDebugClass2 Interface1</span><span class="sxs-lookup"><span data-stu-id="4aa43-102">ICorDebugClass2 Interface1</span></span>
<span data-ttu-id="4aa43-103">ジェネリック、または <xref:System.Type> 型のメソッド パラメーターを持つクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="4aa43-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="4aa43-104">このインターフェイスを拡張[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="4aa43-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4aa43-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="4aa43-105">Methods</span></span>  
  
|<span data-ttu-id="4aa43-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="4aa43-106">Method</span></span>|<span data-ttu-id="4aa43-107">説明</span><span class="sxs-lookup"><span data-stu-id="4aa43-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4aa43-108">GetParameterizedType メソッド</span><span class="sxs-lookup"><span data-stu-id="4aa43-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="4aa43-109">このクラスの型宣言を取得します。</span><span class="sxs-lookup"><span data-stu-id="4aa43-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="4aa43-110">SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="4aa43-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="4aa43-111">このクラスの各メソッドのメソッドがユーザー定義のコードであるかどうかを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="4aa43-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4aa43-112">コメント</span><span class="sxs-lookup"><span data-stu-id="4aa43-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4aa43-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="4aa43-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4aa43-114">要件</span><span class="sxs-lookup"><span data-stu-id="4aa43-114">Requirements</span></span>  
 <span data-ttu-id="4aa43-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4aa43-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4aa43-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4aa43-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4aa43-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4aa43-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4aa43-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4aa43-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aa43-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4aa43-119">See Also</span></span>  
 [<span data-ttu-id="4aa43-120">ICorDebugClass Interface1</span><span class="sxs-lookup"><span data-stu-id="4aa43-120">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 [<span data-ttu-id="4aa43-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4aa43-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
