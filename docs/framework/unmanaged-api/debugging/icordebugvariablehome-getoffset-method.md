---
title: "ICorDebugVariableHome::GetOffset メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetOffset
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ddedc83e4e51cf12a3f8a0504d90bda7f944a6d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="11e0c-102">ICorDebugVariableHome::GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="11e0c-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="11e0c-103">変数のベース レジスタからのオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="11e0c-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11e0c-104">構文</span><span class="sxs-lookup"><span data-stu-id="11e0c-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11e0c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11e0c-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="11e0c-106">[out]ベース レジスタからのオフセット。</span><span class="sxs-lookup"><span data-stu-id="11e0c-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11e0c-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="11e0c-107">Return Value</span></span>  
 <span data-ttu-id="11e0c-108">メソッドは、次の値を返します。</span><span class="sxs-lookup"><span data-stu-id="11e0c-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="11e0c-109">値</span><span class="sxs-lookup"><span data-stu-id="11e0c-109">Value</span></span>|<span data-ttu-id="11e0c-110">説明</span><span class="sxs-lookup"><span data-stu-id="11e0c-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="11e0c-111">変数は、レジスタの相対メモリの場所には。</span><span class="sxs-lookup"><span data-stu-id="11e0c-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="11e0c-112">変数は、レジスタの相対メモリの場所ではありません。</span><span class="sxs-lookup"><span data-stu-id="11e0c-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="11e0c-113">要件</span><span class="sxs-lookup"><span data-stu-id="11e0c-113">Requirements</span></span>  
 <span data-ttu-id="11e0c-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="11e0c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11e0c-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11e0c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11e0c-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11e0c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11e0c-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11e0c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e0c-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="11e0c-118">See Also</span></span>  
 [<span data-ttu-id="11e0c-119">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11e0c-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
