---
title: "ICorDebugAssembly::GetAppDomain メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly.GetAppDomain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly::GetAppDomain
helpviewer_keywords:
- ICorDebugAssembly::GetAppDomain method [.NET Framework debugging]
- GetAppDomain method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 14e18510-23ac-4cba-9f96-c86147a2df9d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f97795568b9811d0dbf7852fd64d5256c29b8f30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="1a7c0-102">ICorDebugAssembly::GetAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="1a7c0-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="1a7c0-103">インターフェイス ポインターを格納しているアプリケーション ドメインに取得`ICorDebugAssembly`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="1a7c0-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a7c0-104">構文</span><span class="sxs-lookup"><span data-stu-id="1a7c0-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1a7c0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1a7c0-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="1a7c0-106">[out]アプリケーション ドメインを表す ICorDebugAppDomain インターフェイスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1a7c0-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a7c0-107">コメント</span><span class="sxs-lookup"><span data-stu-id="1a7c0-107">Remarks</span></span>  
 <span data-ttu-id="1a7c0-108">このアセンブリがシステム アセンブリ場合`GetAppDomain`は null を返します。</span><span class="sxs-lookup"><span data-stu-id="1a7c0-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a7c0-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="1a7c0-109">Requirements</span></span>  
 <span data-ttu-id="1a7c0-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1a7c0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a7c0-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a7c0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a7c0-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a7c0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a7c0-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a7c0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
