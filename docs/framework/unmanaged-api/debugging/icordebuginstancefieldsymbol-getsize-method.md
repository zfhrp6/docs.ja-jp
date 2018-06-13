---
title: ICorDebugInstanceFieldSymbol::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0901e64a7da7f68b2fbcdb63636503893263435f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413791"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="a58b2-102">ICorDebugInstanceFieldSymbol::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="a58b2-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="a58b2-103">インスタンス フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="a58b2-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a58b2-104">構文</span><span class="sxs-lookup"><span data-stu-id="a58b2-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a58b2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a58b2-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="a58b2-106">[out] フィールドの長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a58b2-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a58b2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a58b2-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a58b2-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a58b2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a58b2-109">要件</span><span class="sxs-lookup"><span data-stu-id="a58b2-109">Requirements</span></span>  
 <span data-ttu-id="a58b2-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a58b2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a58b2-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a58b2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a58b2-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a58b2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a58b2-113">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a58b2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a58b2-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a58b2-114">See Also</span></span>  
 [<span data-ttu-id="a58b2-115">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a58b2-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="a58b2-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a58b2-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
