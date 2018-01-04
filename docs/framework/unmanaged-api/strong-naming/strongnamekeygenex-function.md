---
title: "StrongNameKeyGenEx 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyGenEx
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyGenEx
helpviewer_keywords: StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae564f7c4e8333e33b2f2f6229034c3a1396a687
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="709f4-102">StrongNameKeyGenEx 関数</span><span class="sxs-lookup"><span data-stu-id="709f4-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="709f4-103">厳密な名前に使用するため、指定されたキー サイズで新しい公開/秘密キー ペアを生成します。</span><span class="sxs-lookup"><span data-stu-id="709f4-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="709f4-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="709f4-104">This function has been deprecated.</span></span> <span data-ttu-id="709f4-105">使用して、 [iclrstrongname::strongnamekeygenex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="709f4-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="709f4-106">構文</span><span class="sxs-lookup"><span data-stu-id="709f4-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="709f4-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="709f4-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="709f4-108">[in]要求されたキー コンテナーの名前です。</span><span class="sxs-lookup"><span data-stu-id="709f4-108">[in] The requested key container name.</span></span> <span data-ttu-id="709f4-109">`wszKeyContainer`一時的な名前を生成する場合は null か空でない文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="709f4-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="709f4-110">[in]登録キーのままにするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="709f4-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="709f4-111">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="709f4-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="709f4-112">0x00000000 の際に使用される`wszKeyContainer`は一時的なキー コンテナー名を生成する場合は null です。</span><span class="sxs-lookup"><span data-stu-id="709f4-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="709f4-113">0x00000001 (`SN_LEAVE_KEY`)-キーを左に登録する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="709f4-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="709f4-114">[in]ビット単位のキーの要求されたサイズ。</span><span class="sxs-lookup"><span data-stu-id="709f4-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="709f4-115">[out]返された公開/秘密キー ペア。</span><span class="sxs-lookup"><span data-stu-id="709f4-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="709f4-116">[out]サイズをバイト単位での`ppbKeyBlob`します。</span><span class="sxs-lookup"><span data-stu-id="709f4-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="709f4-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="709f4-117">Return Value</span></span>  
 <span data-ttu-id="709f4-118">`true`正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="709f4-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="709f4-119">コメント</span><span class="sxs-lookup"><span data-stu-id="709f4-119">Remarks</span></span>  
 <span data-ttu-id="709f4-120">.NET Framework のバージョン 1.0 および 1.1 が必要な`dwKeySize`厳密な名前でアセンブリに署名する 1024 ビットのバージョン 2.0 には、2048 ビットのキーのサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="709f4-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="709f4-121">呼び出す必要があります、キーが取得された後、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)割り当てられたメモリを解放する関数。</span><span class="sxs-lookup"><span data-stu-id="709f4-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="709f4-122">場合、`StrongNameKeyGenEx`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="709f4-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="709f4-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="709f4-123">Requirements</span></span>  
 <span data-ttu-id="709f4-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="709f4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="709f4-125">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="709f4-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="709f4-126">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="709f4-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="709f4-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="709f4-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="709f4-128">参照</span><span class="sxs-lookup"><span data-stu-id="709f4-128">See Also</span></span>  
 [<span data-ttu-id="709f4-129">StrongNameKeyGenEx メソッド</span><span class="sxs-lookup"><span data-stu-id="709f4-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="709f4-130">StrongNameKeyGen メソッド</span><span class="sxs-lookup"><span data-stu-id="709f4-130">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="709f4-131">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="709f4-131">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
