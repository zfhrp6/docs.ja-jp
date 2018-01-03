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
ms.workload: dotnet
ms.openlocfilehash: 5053ea14ac7a8af33319bbbb289db01dbbc86169
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclass2-interface1"></a><span data-ttu-id="81e55-102">ICorDebugClass2 Interface1</span><span class="sxs-lookup"><span data-stu-id="81e55-102">ICorDebugClass2 Interface1</span></span>
<span data-ttu-id="81e55-103">ジェネリック、または <xref:System.Type> 型のメソッド パラメーターを持つクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="81e55-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="81e55-104">このインターフェイスを拡張[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="81e55-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="81e55-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="81e55-105">Methods</span></span>  
  
|<span data-ttu-id="81e55-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="81e55-106">Method</span></span>|<span data-ttu-id="81e55-107">説明</span><span class="sxs-lookup"><span data-stu-id="81e55-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="81e55-108">GetParameterizedType メソッド</span><span class="sxs-lookup"><span data-stu-id="81e55-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="81e55-109">このクラスの型宣言を取得します。</span><span class="sxs-lookup"><span data-stu-id="81e55-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="81e55-110">SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="81e55-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="81e55-111">このクラスの各メソッドのメソッドがユーザー定義のコードであるかどうかを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="81e55-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81e55-112">コメント</span><span class="sxs-lookup"><span data-stu-id="81e55-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81e55-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="81e55-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81e55-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="81e55-114">Requirements</span></span>  
 <span data-ttu-id="81e55-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="81e55-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81e55-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81e55-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81e55-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81e55-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81e55-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81e55-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e55-119">参照</span><span class="sxs-lookup"><span data-stu-id="81e55-119">See Also</span></span>  
 [<span data-ttu-id="81e55-120">ICorDebugClass Interface1</span><span class="sxs-lookup"><span data-stu-id="81e55-120">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 [<span data-ttu-id="81e55-121">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81e55-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
