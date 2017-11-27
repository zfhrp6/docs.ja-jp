---
title: "ICorDebugStaticFieldSymbol::GetSize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 256a15952cd52c5a096e1f0b8c7fc2086cde226c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="22789-102">ICorDebugStaticFieldSymbol::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="22789-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="22789-103">静的フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="22789-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22789-104">構文</span><span class="sxs-lookup"><span data-stu-id="22789-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22789-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="22789-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="22789-106">[out] フィールドの長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="22789-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22789-107">コメント</span><span class="sxs-lookup"><span data-stu-id="22789-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22789-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="22789-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22789-109">要件</span><span class="sxs-lookup"><span data-stu-id="22789-109">Requirements</span></span>  
 <span data-ttu-id="22789-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="22789-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22789-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22789-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22789-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22789-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22789-113">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22789-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22789-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="22789-114">See Also</span></span>  
 [<span data-ttu-id="22789-115">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="22789-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="22789-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="22789-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
