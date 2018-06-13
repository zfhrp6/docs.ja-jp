---
title: ICorDebugInstanceFieldSymbol::GetOffset メソッド
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c77ac2eac1022fa591066901f48eaf609b5367af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413564"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="93bc7-102">ICorDebugInstanceFieldSymbol::GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="93bc7-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="93bc7-103">このインスタンス フィールドの親クラスにおける、このインスタンス フィールドのオフセット (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="93bc7-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93bc7-104">構文</span><span class="sxs-lookup"><span data-stu-id="93bc7-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93bc7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="93bc7-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="93bc7-106">このインスタンス フィールドの親クラスにおける、このフィールドのオフセットのバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="93bc7-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93bc7-107">コメント</span><span class="sxs-lookup"><span data-stu-id="93bc7-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93bc7-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="93bc7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93bc7-109">要件</span><span class="sxs-lookup"><span data-stu-id="93bc7-109">Requirements</span></span>  
 <span data-ttu-id="93bc7-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="93bc7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93bc7-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93bc7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93bc7-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93bc7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93bc7-113">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93bc7-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93bc7-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="93bc7-114">See Also</span></span>  
 [<span data-ttu-id="93bc7-115">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93bc7-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="93bc7-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93bc7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
