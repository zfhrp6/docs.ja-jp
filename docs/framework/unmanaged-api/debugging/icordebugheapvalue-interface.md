---
title: ICorDebugHeapValue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c510912412f2344dfd92d6ab2c41c35c1f237ae7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415702"
---
# <a name="icordebugheapvalue-interface1"></a><span data-ttu-id="2d34e-102">ICorDebugHeapValue Interface1</span><span class="sxs-lookup"><span data-stu-id="2d34e-102">ICorDebugHeapValue Interface1</span></span>
<span data-ttu-id="2d34e-103">共通言語ランタイム (CLR) のガベージ コレクターによって収集されたオブジェクトを表す"ICorDebugValue"のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="2d34e-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d34e-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="2d34e-104">Methods</span></span>  
  
|<span data-ttu-id="2d34e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2d34e-105">Method</span></span>|<span data-ttu-id="2d34e-106">説明</span><span class="sxs-lookup"><span data-stu-id="2d34e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d34e-107">CreateRelocBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="2d34e-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="2d34e-108">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="2d34e-108">Not implemented.</span></span>|  
|[<span data-ttu-id="2d34e-109">IsValid メソッド</span><span class="sxs-lookup"><span data-stu-id="2d34e-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="2d34e-110">オブジェクトが、これによって表されるかどうかを示す値を取得`ICorDebugHeapValue`が有効で、ガベージ コレクターによってクリアされているか。</span><span class="sxs-lookup"><span data-stu-id="2d34e-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="2d34e-111">.NET Framework version 2.0 では、このメソッドは廃止されました。</span><span class="sxs-lookup"><span data-stu-id="2d34e-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d34e-112">コメント</span><span class="sxs-lookup"><span data-stu-id="2d34e-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d34e-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="2d34e-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d34e-114">要件</span><span class="sxs-lookup"><span data-stu-id="2d34e-114">Requirements</span></span>  
 <span data-ttu-id="2d34e-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d34e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d34e-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d34e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d34e-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d34e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d34e-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d34e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d34e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d34e-119">See Also</span></span>  
    
    
    
 [<span data-ttu-id="2d34e-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2d34e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
