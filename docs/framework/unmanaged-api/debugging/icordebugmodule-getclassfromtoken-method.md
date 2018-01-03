---
title: "ICorDebugModule::GetClassFromToken メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetClassFromToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetClassFromToken
helpviewer_keywords:
- GetClassFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetClassFromToken method [.NET Framework debugging]
ms.assetid: 622a4d3c-0425-4c54-a7e4-0735377cdad2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef8ef4c1f2fb8a7b8aa94b99f3821a91abe0b91d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetclassfromtoken-method"></a><span data-ttu-id="fd861-102">ICorDebugModule::GetClassFromToken メソッド</span><span class="sxs-lookup"><span data-stu-id="fd861-102">ICorDebugModule::GetClassFromToken Method</span></span>
<span data-ttu-id="fd861-103">メタデータ トークンによって指定されたクラスを取得します。</span><span class="sxs-lookup"><span data-stu-id="fd861-103">Gets the class specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd861-104">構文</span><span class="sxs-lookup"><span data-stu-id="fd861-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  mdTypeDef        typeDef,  
    [out] ICorDebugClass **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd861-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd861-105">Parameters</span></span>  
 `typedef`  
 <span data-ttu-id="fd861-106">[in]`mdTypeDef`クラスのメタデータを参照するメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="fd861-106">[in] An `mdTypeDef` metadata token that references the metadata of a class.</span></span>  
  
 `ppClass`  
 <span data-ttu-id="fd861-107">[out]クラスを表す ICorDebugClass オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fd861-107">[out] A pointer to the address of an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd861-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="fd861-108">Requirements</span></span>  
 <span data-ttu-id="fd861-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fd861-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd861-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd861-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd861-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd861-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd861-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd861-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
