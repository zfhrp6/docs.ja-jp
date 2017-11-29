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
ms.openlocfilehash: 364144dcef21e7e9c058cb0317970a273aa8ecac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="8ff31-102">ICorDebugInstanceFieldSymbol::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="8ff31-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="8ff31-103">インスタンス フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="8ff31-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff31-104">構文</span><span class="sxs-lookup"><span data-stu-id="8ff31-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ff31-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8ff31-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="8ff31-106">[out] フィールドの長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8ff31-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ff31-107">コメント</span><span class="sxs-lookup"><span data-stu-id="8ff31-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ff31-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8ff31-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ff31-109">要件</span><span class="sxs-lookup"><span data-stu-id="8ff31-109">Requirements</span></span>  
 <span data-ttu-id="8ff31-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8ff31-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ff31-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ff31-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ff31-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ff31-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ff31-113">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ff31-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff31-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ff31-114">See Also</span></span>  
 [<span data-ttu-id="8ff31-115">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8ff31-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="8ff31-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8ff31-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
