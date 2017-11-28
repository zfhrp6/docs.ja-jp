---
title: "ICorDebugVariableHome::GetRegister メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetRegister
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f16e4bfe4767e1b49d7dacf0481e8911a90e178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="d5e59-102">ICorDebugVariableHome::GetRegister メソッド</span><span class="sxs-lookup"><span data-stu-id="d5e59-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="d5e59-103">場所の種類を持つ変数を格納するレジスタを取得`VLT_REGISTER`、およびロケーションの型の変数のベース レジスタ`VLT_REGISTER_RELATIVE`です。</span><span class="sxs-lookup"><span data-stu-id="d5e59-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5e59-104">構文</span><span class="sxs-lookup"><span data-stu-id="d5e59-104">Syntax</span></span>  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5e59-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d5e59-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="d5e59-106">[out]CorDebugRegister 列挙値の場所の種類を持つ変数のレジスタを示す`VLT_REGISTER`、およびロケーションの型の変数のベース レジスタ`VLT_REGISTER_RELATIVE`です。</span><span class="sxs-lookup"><span data-stu-id="d5e59-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5e59-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="d5e59-107">Return Value</span></span>  
 <span data-ttu-id="d5e59-108">メソッドは、次の値を返します。</span><span class="sxs-lookup"><span data-stu-id="d5e59-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="d5e59-109">値</span><span class="sxs-lookup"><span data-stu-id="d5e59-109">Value</span></span>|<span data-ttu-id="d5e59-110">説明</span><span class="sxs-lookup"><span data-stu-id="d5e59-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="d5e59-111">によって示されるレジスタには、変数、`pRegister`引数。</span><span class="sxs-lookup"><span data-stu-id="d5e59-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="d5e59-112">変数は、レジスタまたはレジスタの相対位置ではありません。</span><span class="sxs-lookup"><span data-stu-id="d5e59-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5e59-113">要件</span><span class="sxs-lookup"><span data-stu-id="d5e59-113">Requirements</span></span>  
 <span data-ttu-id="d5e59-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d5e59-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5e59-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5e59-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5e59-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5e59-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5e59-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5e59-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e59-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5e59-118">See Also</span></span>  
 [<span data-ttu-id="d5e59-119">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="d5e59-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 [<span data-ttu-id="d5e59-120">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5e59-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
