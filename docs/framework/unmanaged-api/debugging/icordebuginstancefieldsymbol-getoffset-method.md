---
title: "ICorDebugInstanceFieldSymbol::GetOffset メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 534e3238a4b20e390c4f2168629e0ba93620f55a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="66e1e-102">ICorDebugInstanceFieldSymbol::GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="66e1e-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="66e1e-103">このインスタンス フィールドの親クラスにおける、このインスタンス フィールドのオフセット (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="66e1e-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e1e-104">構文</span><span class="sxs-lookup"><span data-stu-id="66e1e-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66e1e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="66e1e-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="66e1e-106">このインスタンス フィールドの親クラスにおける、このフィールドのオフセットのバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="66e1e-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66e1e-107">コメント</span><span class="sxs-lookup"><span data-stu-id="66e1e-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66e1e-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="66e1e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66e1e-109">要件</span><span class="sxs-lookup"><span data-stu-id="66e1e-109">Requirements</span></span>  
 <span data-ttu-id="66e1e-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="66e1e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66e1e-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66e1e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66e1e-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66e1e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66e1e-113">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66e1e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e1e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="66e1e-114">See Also</span></span>  
 [<span data-ttu-id="66e1e-115">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="66e1e-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="66e1e-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="66e1e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
