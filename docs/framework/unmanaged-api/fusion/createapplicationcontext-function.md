---
title: "CreateApplicationContext 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateApplicationContext
api_location: fusion.dll
api_type: DLLExport
f1_keywords: CreateApplicationContext
helpviewer_keywords: CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c089c32d4bc8474168274186a9303d39976abfca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="fb60d-102">CreateApplicationContext 関数</span><span class="sxs-lookup"><span data-stu-id="fb60d-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="fb60d-103">この関数は、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="fb60d-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb60d-104">構文</span><span class="sxs-lookup"><span data-stu-id="fb60d-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb60d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fb60d-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="fb60d-106">[in]フレンドリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="fb60d-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="fb60d-107">[out]アプリケーション コンテキストへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fb60d-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb60d-108">要件</span><span class="sxs-lookup"><span data-stu-id="fb60d-108">Requirements</span></span>  
 <span data-ttu-id="fb60d-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fb60d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb60d-110">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="fb60d-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fb60d-111">**ライブラリ:** Fusion.dll 内のリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb60d-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="fb60d-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb60d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb60d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb60d-113">See Also</span></span>  
 [<span data-ttu-id="fb60d-114">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb60d-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="fb60d-115">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="fb60d-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="fb60d-116">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="fb60d-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
