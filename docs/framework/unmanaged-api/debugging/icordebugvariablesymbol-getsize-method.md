---
title: ICorDebugVariableSymbol::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01349b6418008db51c432d5c49f8491a44ab60d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="1caa2-102">ICorDebugVariableSymbol::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="1caa2-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="1caa2-103">変数のサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="1caa2-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1caa2-104">構文</span><span class="sxs-lookup"><span data-stu-id="1caa2-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1caa2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1caa2-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="1caa2-106">変数のサイズが格納されている 32 ビットの符号なし整数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1caa2-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1caa2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="1caa2-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1caa2-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1caa2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1caa2-109">要件</span><span class="sxs-lookup"><span data-stu-id="1caa2-109">Requirements</span></span>  
 <span data-ttu-id="1caa2-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1caa2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1caa2-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1caa2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1caa2-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1caa2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1caa2-113">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1caa2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1caa2-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="1caa2-114">See Also</span></span>  
 [<span data-ttu-id="1caa2-115">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1caa2-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="1caa2-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1caa2-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
