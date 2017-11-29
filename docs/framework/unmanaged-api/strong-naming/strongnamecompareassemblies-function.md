---
title: "StrongNameCompareAssemblies 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameCompareAssemblies
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameCompareAssemblies
helpviewer_keywords: StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a3453cffb5e98e3623565785ab64db4f455be981
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="b40dd-102">StrongNameCompareAssemblies 関数</span><span class="sxs-lookup"><span data-stu-id="b40dd-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="b40dd-103">2 つのアセンブリが厳密な名前の署名によってのみが異なるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="b40dd-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="b40dd-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="b40dd-104">This function has been deprecated.</span></span> <span data-ttu-id="b40dd-105">使用して、 [iclrstrongname::strongnamecompareassemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="b40dd-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b40dd-106">構文</span><span class="sxs-lookup"><span data-stu-id="b40dd-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b40dd-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b40dd-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="b40dd-108">[in]最初のアセンブリへのパス。</span><span class="sxs-lookup"><span data-stu-id="b40dd-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="b40dd-109">[in]2 番目のアセンブリへのパス。</span><span class="sxs-lookup"><span data-stu-id="b40dd-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="b40dd-110">[out]次の値のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="b40dd-110">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="b40dd-111">`SN_CMP_DIFFERENT`(0) にアセンブリが別のデータを含むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="b40dd-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="b40dd-112">`SN_CMP_IDENTICAL`(1) - アセンブリが同じで、署名とチェックサムを含むでことを指定します。</span><span class="sxs-lookup"><span data-stu-id="b40dd-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="b40dd-113">`SN_CMP_SIGONLY`(2) のアセンブリが署名およびチェックサムでのみが異なることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b40dd-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b40dd-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="b40dd-114">Return Value</span></span>  
 <span data-ttu-id="b40dd-115">`true`正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="b40dd-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b40dd-116">要件</span><span class="sxs-lookup"><span data-stu-id="b40dd-116">Requirements</span></span>  
 <span data-ttu-id="b40dd-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b40dd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b40dd-118">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="b40dd-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b40dd-119">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b40dd-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b40dd-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b40dd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b40dd-121">コメント</span><span class="sxs-lookup"><span data-stu-id="b40dd-121">Remarks</span></span>  
 <span data-ttu-id="b40dd-122">アセンブリの厳密な名前の署名は、アセンブリのテキストの名前、バージョン、カルチャ、および公開キー トークンで構成されます。</span><span class="sxs-lookup"><span data-stu-id="b40dd-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="b40dd-123">場合、`StrongNameCompareAssemblies`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="b40dd-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b40dd-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="b40dd-124">See Also</span></span>  
 [<span data-ttu-id="b40dd-125">StrongNameCompareAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="b40dd-125">StrongNameCompareAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)  
 [<span data-ttu-id="b40dd-126">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b40dd-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
