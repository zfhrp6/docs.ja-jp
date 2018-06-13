---
title: ICorDebugStringValue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue
helpviewer_keywords:
- ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2814f6164f383c36bb5b8e20ce8996b30eef0f1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421701"
---
# <a name="icordebugstringvalue-interface1"></a><span data-ttu-id="30cdb-102">ICorDebugStringValue Interface1</span><span class="sxs-lookup"><span data-stu-id="30cdb-102">ICorDebugStringValue Interface1</span></span>
<span data-ttu-id="30cdb-103">文字列の値に適用される ICorDebugHeapValue のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="30cdb-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="30cdb-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="30cdb-104">Methods</span></span>  
  
|<span data-ttu-id="30cdb-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="30cdb-105">Method</span></span>|<span data-ttu-id="30cdb-106">説明</span><span class="sxs-lookup"><span data-stu-id="30cdb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="30cdb-107">GetLength メソッド</span><span class="sxs-lookup"><span data-stu-id="30cdb-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="30cdb-108">これによって参照される文字列の文字数を取得`ICorDebugStringValue`です。</span><span class="sxs-lookup"><span data-stu-id="30cdb-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="30cdb-109">GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="30cdb-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="30cdb-110">これによって参照される文字列を取得`ICorDebugStringValue`です。</span><span class="sxs-lookup"><span data-stu-id="30cdb-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30cdb-111">コメント</span><span class="sxs-lookup"><span data-stu-id="30cdb-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30cdb-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="30cdb-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30cdb-113">要件</span><span class="sxs-lookup"><span data-stu-id="30cdb-113">Requirements</span></span>  
 <span data-ttu-id="30cdb-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="30cdb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30cdb-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30cdb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30cdb-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30cdb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30cdb-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30cdb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30cdb-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="30cdb-118">See Also</span></span>  
 [<span data-ttu-id="30cdb-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30cdb-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
