---
title: ICorDebugILFrame2 Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccb39609b37aff09ac7890df562d6c08e3c3c159
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412436"
---
# <a name="icordebugilframe2-interface1"></a><span data-ttu-id="4be7b-102">ICorDebugILFrame2 Interface1</span><span class="sxs-lookup"><span data-stu-id="4be7b-102">ICorDebugILFrame2 Interface1</span></span>
<span data-ttu-id="4be7b-103">ICorDebugILFrame インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="4be7b-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4be7b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="4be7b-104">Methods</span></span>  
  
|<span data-ttu-id="4be7b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="4be7b-105">Method</span></span>|<span data-ttu-id="4be7b-106">説明</span><span class="sxs-lookup"><span data-stu-id="4be7b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4be7b-107">EnumerateTypeParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="4be7b-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="4be7b-108">含む ICorDebugTypeEnum オブジェクトを取得、<xref:System.Type>このフレーム内のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="4be7b-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="4be7b-109">RemapFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="4be7b-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="4be7b-110">新しい MSIL オフセットを指定することによって編集された関数を再マップします。</span><span class="sxs-lookup"><span data-stu-id="4be7b-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4be7b-111">コメント</span><span class="sxs-lookup"><span data-stu-id="4be7b-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4be7b-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="4be7b-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4be7b-113">要件</span><span class="sxs-lookup"><span data-stu-id="4be7b-113">Requirements</span></span>  
 <span data-ttu-id="4be7b-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4be7b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4be7b-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4be7b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4be7b-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4be7b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4be7b-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4be7b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4be7b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="4be7b-118">See Also</span></span>  
 [<span data-ttu-id="4be7b-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4be7b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
