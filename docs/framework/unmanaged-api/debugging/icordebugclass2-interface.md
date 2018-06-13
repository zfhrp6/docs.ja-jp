---
title: ICorDebugClass2 Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 905e88eb2f43850124414a42bb4e729158f9555a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405386"
---
# <a name="icordebugclass2-interface1"></a><span data-ttu-id="bc1c0-102">ICorDebugClass2 Interface1</span><span class="sxs-lookup"><span data-stu-id="bc1c0-102">ICorDebugClass2 Interface1</span></span>
<span data-ttu-id="bc1c0-103">ジェネリック、または <xref:System.Type> 型のメソッド パラメーターを持つクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="bc1c0-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="bc1c0-104">このインターフェイスを拡張[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="bc1c0-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bc1c0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="bc1c0-105">Methods</span></span>  
  
|<span data-ttu-id="bc1c0-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="bc1c0-106">Method</span></span>|<span data-ttu-id="bc1c0-107">説明</span><span class="sxs-lookup"><span data-stu-id="bc1c0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bc1c0-108">GetParameterizedType メソッド</span><span class="sxs-lookup"><span data-stu-id="bc1c0-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="bc1c0-109">このクラスの型宣言を取得します。</span><span class="sxs-lookup"><span data-stu-id="bc1c0-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="bc1c0-110">SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="bc1c0-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="bc1c0-111">このクラスの各メソッドのメソッドがユーザー定義のコードであるかどうかを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="bc1c0-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc1c0-112">コメント</span><span class="sxs-lookup"><span data-stu-id="bc1c0-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc1c0-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="bc1c0-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc1c0-114">要件</span><span class="sxs-lookup"><span data-stu-id="bc1c0-114">Requirements</span></span>  
 <span data-ttu-id="bc1c0-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bc1c0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc1c0-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc1c0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc1c0-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc1c0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc1c0-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc1c0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc1c0-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc1c0-119">See Also</span></span>  
 [<span data-ttu-id="bc1c0-120">ICorDebugClass Interface1</span><span class="sxs-lookup"><span data-stu-id="bc1c0-120">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 [<span data-ttu-id="bc1c0-121">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bc1c0-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
