---
title: "ICorDebugAssembly::EnumerateModules メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly.EnumerateModules
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly::EnumerateModules
helpviewer_keywords:
- ICorDebugAssembly::EnumerateModules method [.NET Framework debugging]
- EnumerateModules method [.NET Framework debugging]
ms.assetid: c7ba51a1-0dd5-4452-b471-232febe0f897
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5bc6aced78d1d7ffc6521bca52bed1b2e232bbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="9b23a-102">ICorDebugAssembly::EnumerateModules メソッド</span><span class="sxs-lookup"><span data-stu-id="9b23a-102">ICorDebugAssembly::EnumerateModules Method</span></span>
<span data-ttu-id="9b23a-103">含まれるモジュールの列挙子を取得、`ICorDebugAssembly`です。</span><span class="sxs-lookup"><span data-stu-id="9b23a-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b23a-104">構文</span><span class="sxs-lookup"><span data-stu-id="9b23a-104">Syntax</span></span>  
  
```  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b23a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b23a-105">Parameters</span></span>  
 `ppModules`  
 <span data-ttu-id="9b23a-106">[out]列挙子である ICorDebugModuleEnum インターフェイスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9b23a-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b23a-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="9b23a-107">Requirements</span></span>  
 <span data-ttu-id="9b23a-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9b23a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b23a-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b23a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b23a-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b23a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b23a-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b23a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
