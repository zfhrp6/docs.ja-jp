---
title: "ICorDebugVariableSymbol::GetName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 747249c23089cbeba04c3a872823f01f2b334203
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="239ae-102">ICorDebugVariableSymbol::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="239ae-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="239ae-103">変数の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="239ae-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="239ae-104">構文</span><span class="sxs-lookup"><span data-stu-id="239ae-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="239ae-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="239ae-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="239ae-106">[in] `szName` バッファー内の文字数。</span><span class="sxs-lookup"><span data-stu-id="239ae-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="239ae-107">[out] `szName` バッファーに実際に書き込まれた文字数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="239ae-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="239ae-108">変数名が格納されている文字配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="239ae-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="239ae-109">コメント</span><span class="sxs-lookup"><span data-stu-id="239ae-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="239ae-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="239ae-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="239ae-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="239ae-111">Requirements</span></span>  
 <span data-ttu-id="239ae-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="239ae-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="239ae-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="239ae-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="239ae-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="239ae-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="239ae-115">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="239ae-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239ae-116">参照</span><span class="sxs-lookup"><span data-stu-id="239ae-116">See Also</span></span>  
 [<span data-ttu-id="239ae-117">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="239ae-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="239ae-118">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="239ae-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
