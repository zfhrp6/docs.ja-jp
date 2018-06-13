---
title: ICLRStrongName::StrongNameCompareAssemblies メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5020c31f590f527856f966ede512e98c07496ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435389"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="b789b-102">ICLRStrongName::StrongNameCompareAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="b789b-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="b789b-103">2 つのアセンブリが厳密な名前の署名によってのみが異なるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="b789b-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b789b-104">構文</span><span class="sxs-lookup"><span data-stu-id="b789b-104">Syntax</span></span>  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b789b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b789b-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="b789b-106">[in]最初のアセンブリへのパス。</span><span class="sxs-lookup"><span data-stu-id="b789b-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="b789b-107">[in]2 番目のアセンブリへのパス。</span><span class="sxs-lookup"><span data-stu-id="b789b-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="b789b-108">[out]次の値のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="b789b-108">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="b789b-109">`SN_CMP_DIFFERENT` (0) にアセンブリが別のデータを含むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="b789b-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="b789b-110">`SN_CMP_IDENTICAL` (1) - アセンブリが同じで、署名とチェックサムを含むでことを指定します。</span><span class="sxs-lookup"><span data-stu-id="b789b-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="b789b-111">`SN_CMP_SIGONLY` (2) のアセンブリが署名およびチェックサムでのみが異なることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b789b-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b789b-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="b789b-112">Return Value</span></span>  
 <span data-ttu-id="b789b-113">`S_OK` メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="b789b-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b789b-114">要件</span><span class="sxs-lookup"><span data-stu-id="b789b-114">Requirements</span></span>  
 <span data-ttu-id="b789b-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b789b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b789b-116">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b789b-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b789b-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b789b-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b789b-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b789b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b789b-119">コメント</span><span class="sxs-lookup"><span data-stu-id="b789b-119">Remarks</span></span>  
 <span data-ttu-id="b789b-120">アセンブリの厳密な名前の署名は、アセンブリのテキストの名前、バージョン、カルチャ、および公開キー トークンで構成されます。</span><span class="sxs-lookup"><span data-stu-id="b789b-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b789b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="b789b-121">See Also</span></span>  
 [<span data-ttu-id="b789b-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b789b-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
