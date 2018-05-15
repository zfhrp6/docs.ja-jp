---
title: ICorDebugVariableHome::GetOffset メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a2ea7273fec62654c168d6786d3644b184ff7f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="0d2f6-102">ICorDebugVariableHome::GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="0d2f6-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="0d2f6-103">変数のベース レジスタからのオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="0d2f6-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d2f6-104">構文</span><span class="sxs-lookup"><span data-stu-id="0d2f6-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d2f6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0d2f6-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="0d2f6-106">[out]ベース レジスタからのオフセット。</span><span class="sxs-lookup"><span data-stu-id="0d2f6-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d2f6-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="0d2f6-107">Return Value</span></span>  
 <span data-ttu-id="0d2f6-108">メソッドは、次の値を返します。</span><span class="sxs-lookup"><span data-stu-id="0d2f6-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="0d2f6-109">[値]</span><span class="sxs-lookup"><span data-stu-id="0d2f6-109">Value</span></span>|<span data-ttu-id="0d2f6-110">説明</span><span class="sxs-lookup"><span data-stu-id="0d2f6-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="0d2f6-111">変数は、レジスタの相対メモリの場所には。</span><span class="sxs-lookup"><span data-stu-id="0d2f6-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="0d2f6-112">変数は、レジスタの相対メモリの場所ではありません。</span><span class="sxs-lookup"><span data-stu-id="0d2f6-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d2f6-113">要件</span><span class="sxs-lookup"><span data-stu-id="0d2f6-113">Requirements</span></span>  
 <span data-ttu-id="0d2f6-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0d2f6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d2f6-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d2f6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d2f6-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d2f6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d2f6-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d2f6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d2f6-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d2f6-118">See Also</span></span>  
 [<span data-ttu-id="0d2f6-119">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d2f6-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
