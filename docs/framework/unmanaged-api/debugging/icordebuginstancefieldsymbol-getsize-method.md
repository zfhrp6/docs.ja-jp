---
title: "ICorDebugInstanceFieldSymbol::GetSize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad13dbe8148d4d9507c6a450d2833da049e0e13a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="23a65-102">ICorDebugInstanceFieldSymbol::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="23a65-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="23a65-103">インスタンス フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="23a65-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23a65-104">構文</span><span class="sxs-lookup"><span data-stu-id="23a65-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23a65-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="23a65-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="23a65-106">[out] フィールドの長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="23a65-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23a65-107">コメント</span><span class="sxs-lookup"><span data-stu-id="23a65-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23a65-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="23a65-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23a65-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="23a65-109">Requirements</span></span>  
 <span data-ttu-id="23a65-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="23a65-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23a65-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23a65-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23a65-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23a65-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23a65-113">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23a65-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a65-114">参照</span><span class="sxs-lookup"><span data-stu-id="23a65-114">See Also</span></span>  
 [<span data-ttu-id="23a65-115">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23a65-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="23a65-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23a65-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
