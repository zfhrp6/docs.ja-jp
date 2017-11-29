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
ms.openlocfilehash: b43548d18ac13ac30fa7b6c23699f1db98a78ca0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugassemblygetappdomain-method"></a><span data-ttu-id="ced3c-102">ICorDebugAssembly::GetAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="ced3c-102">ICorDebugAssembly::GetAppDomain Method</span></span>
<span data-ttu-id="ced3c-103">インターフェイス ポインターを格納しているアプリケーション ドメインに取得`ICorDebugAssembly`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="ced3c-103">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ced3c-104">構文</span><span class="sxs-lookup"><span data-stu-id="ced3c-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ced3c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ced3c-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="ced3c-106">[out]アプリケーション ドメインを表す ICorDebugAppDomain インターフェイスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ced3c-106">[out] A pointer to the address of an ICorDebugAppDomain interface that represents the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ced3c-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ced3c-107">Remarks</span></span>  
 <span data-ttu-id="ced3c-108">このアセンブリがシステム アセンブリ場合`GetAppDomain`は null を返します。</span><span class="sxs-lookup"><span data-stu-id="ced3c-108">If this assembly is the system assembly, `GetAppDomain` returns null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ced3c-109">要件</span><span class="sxs-lookup"><span data-stu-id="ced3c-109">Requirements</span></span>  
 <span data-ttu-id="ced3c-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ced3c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ced3c-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ced3c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ced3c-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ced3c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ced3c-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ced3c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
