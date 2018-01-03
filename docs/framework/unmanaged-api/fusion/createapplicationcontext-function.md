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
ms.workload: dotnet
ms.openlocfilehash: 89c3181a157ce5162d93d1df14641b393fb3082d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="e1324-102">CreateApplicationContext 関数</span><span class="sxs-lookup"><span data-stu-id="e1324-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="e1324-103">この関数は、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="e1324-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1324-104">構文</span><span class="sxs-lookup"><span data-stu-id="e1324-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1324-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e1324-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="e1324-106">[in]フレンドリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e1324-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="e1324-107">[out]アプリケーション コンテキストへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e1324-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1324-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="e1324-108">Requirements</span></span>  
 <span data-ttu-id="e1324-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e1324-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1324-110">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e1324-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e1324-111">**ライブラリ:** Fusion.dll 内のリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e1324-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="e1324-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1324-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1324-113">参照</span><span class="sxs-lookup"><span data-stu-id="e1324-113">See Also</span></span>  
 [<span data-ttu-id="e1324-114">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e1324-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="e1324-115">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="e1324-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="e1324-116">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="e1324-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
