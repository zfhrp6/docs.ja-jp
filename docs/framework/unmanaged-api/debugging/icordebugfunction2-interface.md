---
title: ICorDebugFunction2 Interface1
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d765f87e36c98b5f664e84d85b883bc949fccf54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415335"
---
# <a name="icordebugfunction2-interface1"></a><span data-ttu-id="cc60f-102">ICorDebugFunction2 Interface1</span><span class="sxs-lookup"><span data-stu-id="cc60f-102">ICorDebugFunction2 Interface1</span></span>
<span data-ttu-id="cc60f-103">非ユーザー コードをスキップするデバッグ手順で マイ コードのみをサポートする ICorDebugFunction インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="cc60f-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cc60f-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="cc60f-104">Methods</span></span>  
  
|<span data-ttu-id="cc60f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="cc60f-105">Method</span></span>|<span data-ttu-id="cc60f-106">説明</span><span class="sxs-lookup"><span data-stu-id="cc60f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cc60f-107">EnumerateNativeCode メソッド</span><span class="sxs-lookup"><span data-stu-id="cc60f-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="cc60f-108">(まだ実装されていません。)ICorDebugFunction2 オブジェクトによって参照された関数のネイティブ コードのステートメントを含む ICorDebugCodeEnum へのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="cc60f-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="cc60f-109">GetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="cc60f-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="cc60f-110">この関数はユーザー コードとしてマークされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc60f-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="cc60f-111">GetVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="cc60f-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="cc60f-112">この関数のエディット コンティニュ バージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="cc60f-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="cc60f-113">SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="cc60f-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="cc60f-114">マイ コードのみのマークをこの関数のステップ インします。</span><span class="sxs-lookup"><span data-stu-id="cc60f-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc60f-115">コメント</span><span class="sxs-lookup"><span data-stu-id="cc60f-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc60f-116">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cc60f-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc60f-117">要件</span><span class="sxs-lookup"><span data-stu-id="cc60f-117">Requirements</span></span>  
 <span data-ttu-id="cc60f-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cc60f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc60f-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc60f-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc60f-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc60f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc60f-121">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc60f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc60f-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc60f-122">See Also</span></span>  
 [<span data-ttu-id="cc60f-123">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc60f-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
