---
title: "ICorDebugInstanceFieldSymbol::GetName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfd56230d391c44343bdb3f575247b07af1e98ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="e8fcb-102">ICorDebugInstanceFieldSymbol::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="e8fcb-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="e8fcb-103">インスタンス フィールドの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="e8fcb-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8fcb-104">構文</span><span class="sxs-lookup"><span data-stu-id="e8fcb-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8fcb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e8fcb-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e8fcb-106">[in] `szName` バッファー内の文字数。</span><span class="sxs-lookup"><span data-stu-id="e8fcb-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e8fcb-107">[out] `szName` バッファーに実際に書き込まれた文字数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e8fcb-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="e8fcb-108">[out] 返される名前を格納する文字配列。</span><span class="sxs-lookup"><span data-stu-id="e8fcb-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8fcb-109">コメント</span><span class="sxs-lookup"><span data-stu-id="e8fcb-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8fcb-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e8fcb-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8fcb-111">要件</span><span class="sxs-lookup"><span data-stu-id="e8fcb-111">Requirements</span></span>  
 <span data-ttu-id="e8fcb-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e8fcb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8fcb-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8fcb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8fcb-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8fcb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8fcb-115">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8fcb-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8fcb-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8fcb-116">See Also</span></span>  
 [<span data-ttu-id="e8fcb-117">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8fcb-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="e8fcb-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8fcb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
