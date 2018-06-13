---
title: CreateApplicationContext 関数
ms.date: 03/30/2017
api_name:
- CreateApplicationContext
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateApplicationContext
helpviewer_keywords:
- CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80012d030d0ea51ab3d150a7fd346b78e29dbde5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430101"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="eb278-102">CreateApplicationContext 関数</span><span class="sxs-lookup"><span data-stu-id="eb278-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="eb278-103">この関数は、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="eb278-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb278-104">構文</span><span class="sxs-lookup"><span data-stu-id="eb278-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb278-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eb278-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="eb278-106">[in]フレンドリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="eb278-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="eb278-107">[out]アプリケーション コンテキストへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eb278-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb278-108">要件</span><span class="sxs-lookup"><span data-stu-id="eb278-108">Requirements</span></span>  
 <span data-ttu-id="eb278-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="eb278-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb278-110">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="eb278-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="eb278-111">**ライブラリ:** Fusion.dll 内のリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="eb278-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="eb278-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb278-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb278-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb278-113">See Also</span></span>  
 [<span data-ttu-id="eb278-114">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb278-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="eb278-115">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="eb278-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="eb278-116">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="eb278-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
