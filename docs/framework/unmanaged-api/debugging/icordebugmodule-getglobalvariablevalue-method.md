---
title: "ICorDebugModule::GetGlobalVariableValue メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetGlobalVariableValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetGlobalVariableValue
helpviewer_keywords:
- ICorDebugModule::GetGlobalVariableValue method [.NET Framework debugging]
- GetGlobalVariableValue method [.NET Framework debugging]
ms.assetid: bbc0881c-6a59-41a0-b5ee-2f3d1b71684c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 00fb56353652e2fdeac7d7b42c030d9105cc9aca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="b6b38-102">ICorDebugModule::GetGlobalVariableValue メソッド</span><span class="sxs-lookup"><span data-stu-id="b6b38-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>
<span data-ttu-id="b6b38-103">指定のグローバル変数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b6b38-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b38-104">構文</span><span class="sxs-lookup"><span data-stu-id="b6b38-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6b38-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b6b38-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="b6b38-106">[in]`mdFieldDef`グローバル変数を記述するメタデータを参照するトークン。</span><span class="sxs-lookup"><span data-stu-id="b6b38-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b6b38-107">[out]指定のグローバル変数の値を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b6b38-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6b38-108">要件</span><span class="sxs-lookup"><span data-stu-id="b6b38-108">Requirements</span></span>  
 <span data-ttu-id="b6b38-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6b38-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6b38-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6b38-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6b38-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6b38-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6b38-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6b38-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
