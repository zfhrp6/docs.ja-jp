---
title: ICorDebugVariableSymbol::GetName メソッド
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73aa5a9ca6625ab58e451449fab4c98f8b83014e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422441"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="41774-102">ICorDebugVariableSymbol::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="41774-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="41774-103">変数の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="41774-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41774-104">構文</span><span class="sxs-lookup"><span data-stu-id="41774-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41774-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="41774-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="41774-106">[in] `szName` バッファー内の文字数。</span><span class="sxs-lookup"><span data-stu-id="41774-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="41774-107">[out] `szName` バッファーに実際に書き込まれた文字数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="41774-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="41774-108">変数名が格納されている文字配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="41774-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41774-109">コメント</span><span class="sxs-lookup"><span data-stu-id="41774-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41774-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="41774-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41774-111">要件</span><span class="sxs-lookup"><span data-stu-id="41774-111">Requirements</span></span>  
 <span data-ttu-id="41774-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="41774-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41774-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41774-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41774-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41774-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41774-115">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41774-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41774-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="41774-116">See Also</span></span>  
 [<span data-ttu-id="41774-117">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="41774-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="41774-118">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="41774-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
