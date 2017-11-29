---
title: "ICLRStrongName::StrongNameCompareAssemblies メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameCompareAssemblies
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab69a0d0bb5894c2393e240b4f89b9a16dd98939
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="28a94-102">ICLRStrongName::StrongNameCompareAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="28a94-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="28a94-103">2 つのアセンブリが厳密な名前の署名によってのみが異なるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="28a94-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28a94-104">構文</span><span class="sxs-lookup"><span data-stu-id="28a94-104">Syntax</span></span>  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28a94-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="28a94-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="28a94-106">[in]最初のアセンブリへのパス。</span><span class="sxs-lookup"><span data-stu-id="28a94-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="28a94-107">[in]2 番目のアセンブリへのパス。</span><span class="sxs-lookup"><span data-stu-id="28a94-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="28a94-108">[out]次の値のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="28a94-108">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="28a94-109">`SN_CMP_DIFFERENT`(0) にアセンブリが別のデータを含むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="28a94-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="28a94-110">`SN_CMP_IDENTICAL`(1) - アセンブリが同じで、署名とチェックサムを含むでことを指定します。</span><span class="sxs-lookup"><span data-stu-id="28a94-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="28a94-111">`SN_CMP_SIGONLY`(2) のアセンブリが署名およびチェックサムでのみが異なることを指定します。</span><span class="sxs-lookup"><span data-stu-id="28a94-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28a94-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="28a94-112">Return Value</span></span>  
 <span data-ttu-id="28a94-113">`S_OK`メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="28a94-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28a94-114">要件</span><span class="sxs-lookup"><span data-stu-id="28a94-114">Requirements</span></span>  
 <span data-ttu-id="28a94-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="28a94-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28a94-116">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="28a94-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="28a94-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="28a94-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28a94-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28a94-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28a94-119">コメント</span><span class="sxs-lookup"><span data-stu-id="28a94-119">Remarks</span></span>  
 <span data-ttu-id="28a94-120">アセンブリの厳密な名前の署名は、アセンブリのテキストの名前、バージョン、カルチャ、および公開キー トークンで構成されます。</span><span class="sxs-lookup"><span data-stu-id="28a94-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28a94-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="28a94-121">See Also</span></span>  
 [<span data-ttu-id="28a94-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="28a94-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
