---
title: ICorDebugHeapValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue
helpviewer_keywords: ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7868fc84ba3003909992334d1a66e1ed243eca18
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapvalue-interface1"></a><span data-ttu-id="a17ce-102">ICorDebugHeapValue Interface1</span><span class="sxs-lookup"><span data-stu-id="a17ce-102">ICorDebugHeapValue Interface1</span></span>
<span data-ttu-id="a17ce-103">共通言語ランタイム (CLR) のガベージ コレクターによって収集されたオブジェクトを表す"ICorDebugValue"のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="a17ce-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a17ce-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a17ce-104">Methods</span></span>  
  
|<span data-ttu-id="a17ce-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a17ce-105">Method</span></span>|<span data-ttu-id="a17ce-106">説明</span><span class="sxs-lookup"><span data-stu-id="a17ce-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a17ce-107">CreateRelocBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="a17ce-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="a17ce-108">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="a17ce-108">Not implemented.</span></span>|  
|[<span data-ttu-id="a17ce-109">IsValid メソッド</span><span class="sxs-lookup"><span data-stu-id="a17ce-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="a17ce-110">オブジェクトが、これによって表されるかどうかを示す値を取得`ICorDebugHeapValue`が有効で、ガベージ コレクターによってクリアされているか。</span><span class="sxs-lookup"><span data-stu-id="a17ce-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="a17ce-111">.NET Framework version 2.0 では、このメソッドは廃止されました。</span><span class="sxs-lookup"><span data-stu-id="a17ce-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a17ce-112">コメント</span><span class="sxs-lookup"><span data-stu-id="a17ce-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a17ce-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a17ce-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a17ce-114">要件</span><span class="sxs-lookup"><span data-stu-id="a17ce-114">Requirements</span></span>  
 <span data-ttu-id="a17ce-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a17ce-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a17ce-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a17ce-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a17ce-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a17ce-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a17ce-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a17ce-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a17ce-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a17ce-119">See Also</span></span>  
    
    
    
 [<span data-ttu-id="a17ce-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a17ce-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
