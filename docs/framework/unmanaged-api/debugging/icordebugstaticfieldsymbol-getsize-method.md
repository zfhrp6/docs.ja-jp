---
title: ICorDebugStaticFieldSymbol::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acb72a7d6c39efa5fa93bfddc314d07ec6cd8348
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419095"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="c8161-102">ICorDebugStaticFieldSymbol::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="c8161-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="c8161-103">静的フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="c8161-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8161-104">構文</span><span class="sxs-lookup"><span data-stu-id="c8161-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8161-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c8161-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="c8161-106">[out] フィールドの長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c8161-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8161-107">コメント</span><span class="sxs-lookup"><span data-stu-id="c8161-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8161-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8161-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8161-109">要件</span><span class="sxs-lookup"><span data-stu-id="c8161-109">Requirements</span></span>  
 <span data-ttu-id="c8161-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c8161-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8161-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8161-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8161-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8161-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8161-113">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8161-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8161-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8161-114">See Also</span></span>  
 [<span data-ttu-id="c8161-115">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8161-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="c8161-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8161-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
