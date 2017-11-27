---
title: "PreBindAssemblyEx 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PreBindAssemblyEx
api_location: fusion.dll
api_type: DLLExport
f1_keywords: PreBindAssemblyEx
helpviewer_keywords: PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c9bd5cb6be2ccfd25d61a8a2f4347b384e1b2567
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="95fe5-102">PreBindAssemblyEx 関数</span><span class="sxs-lookup"><span data-stu-id="95fe5-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="95fe5-103">アセンブリのポリシー適用後の表示名を取得します。</span><span class="sxs-lookup"><span data-stu-id="95fe5-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="95fe5-104">この関数は、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="95fe5-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95fe5-105">構文</span><span class="sxs-lookup"><span data-stu-id="95fe5-105">Syntax</span></span>  
  
```  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95fe5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="95fe5-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="95fe5-107">[in]アプリケーション コンテキストを識別します。</span><span class="sxs-lookup"><span data-stu-id="95fe5-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="95fe5-108">[in]アセンブリ名を識別します。</span><span class="sxs-lookup"><span data-stu-id="95fe5-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="95fe5-109">[in]親アセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="95fe5-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="95fe5-110">このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="95fe5-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="95fe5-111">[in]ランタイムのバージョンを識別します。</span><span class="sxs-lookup"><span data-stu-id="95fe5-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="95fe5-112">[out]後のポリシーの表示名が含まれています。</span><span class="sxs-lookup"><span data-stu-id="95fe5-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="95fe5-113">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="95fe5-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="95fe5-114">`pvReserved`null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="95fe5-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95fe5-115">コメント</span><span class="sxs-lookup"><span data-stu-id="95fe5-115">Remarks</span></span>  
 <span data-ttu-id="95fe5-116">`ppNamePostPolicy`関数が HRESULT FUSION_E_REF_DEF_MISMATCH を返す場合にのみ、出力パラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="95fe5-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="95fe5-117">それ以外の場合は null です。</span><span class="sxs-lookup"><span data-stu-id="95fe5-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95fe5-118">要件</span><span class="sxs-lookup"><span data-stu-id="95fe5-118">Requirements</span></span>  
 <span data-ttu-id="95fe5-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="95fe5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95fe5-120">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="95fe5-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="95fe5-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="95fe5-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95fe5-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95fe5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95fe5-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="95fe5-123">See Also</span></span>  
 [<span data-ttu-id="95fe5-124">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="95fe5-124">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
