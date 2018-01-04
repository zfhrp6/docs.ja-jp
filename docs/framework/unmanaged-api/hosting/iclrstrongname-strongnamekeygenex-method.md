---
title: "ICLRStrongName::StrongNameKeyGenEx メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyGenEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 581f486a2def90f44c0fb3f1bcf9d3bbcc1fc317
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="1f431-102">ICLRStrongName::StrongNameKeyGenEx メソッド</span><span class="sxs-lookup"><span data-stu-id="1f431-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="1f431-103">厳密な名前に使用するため、指定されたキー サイズで新しい公開/秘密キー ペアを生成します。</span><span class="sxs-lookup"><span data-stu-id="1f431-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f431-104">構文</span><span class="sxs-lookup"><span data-stu-id="1f431-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f431-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1f431-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="1f431-106">[in]要求されたキー コンテナーの名前です。</span><span class="sxs-lookup"><span data-stu-id="1f431-106">[in] The requested key container name.</span></span> <span data-ttu-id="1f431-107">`wszKeyContainer`空でない文字列または一時的な名前を生成するのには null でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="1f431-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1f431-108">[in]登録キーのままにするかどうかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="1f431-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="1f431-109">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1f431-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="1f431-110">0x00000000 の際に使用される`wszKeyContainer`は一時的なキー コンテナー名を生成する場合は null です。</span><span class="sxs-lookup"><span data-stu-id="1f431-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="1f431-111">0x00000001 (`SN_LEAVE_KEY`)-キーを左に登録する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="1f431-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="1f431-112">[in]ビット単位のキーの要求されたサイズ。</span><span class="sxs-lookup"><span data-stu-id="1f431-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="1f431-113">[out]返された公開/秘密キー ペア。</span><span class="sxs-lookup"><span data-stu-id="1f431-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="1f431-114">[out]サイズをバイト単位での`ppbKeyBlob`します。</span><span class="sxs-lookup"><span data-stu-id="1f431-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f431-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="1f431-115">Return Value</span></span>  
 <span data-ttu-id="1f431-116">`S_OK`メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="1f431-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f431-117">コメント</span><span class="sxs-lookup"><span data-stu-id="1f431-117">Remarks</span></span>  
 <span data-ttu-id="1f431-118">.NET Framework のバージョン 1.0 および 1.1 が必要な`dwKeySize`厳密な名前でアセンブリに署名する 1024 ビットのバージョン 2.0 には、2048 ビットのキーのサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="1f431-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="1f431-119">呼び出す必要があります、キーが取得された後、 [iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)を割り当てられたメモリを解放するメソッド。</span><span class="sxs-lookup"><span data-stu-id="1f431-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f431-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="1f431-120">Requirements</span></span>  
 <span data-ttu-id="1f431-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f431-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f431-122">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1f431-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1f431-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1f431-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f431-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f431-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f431-125">参照</span><span class="sxs-lookup"><span data-stu-id="1f431-125">See Also</span></span>  
 [<span data-ttu-id="1f431-126">StrongNameKeyGen メソッド</span><span class="sxs-lookup"><span data-stu-id="1f431-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="1f431-127">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f431-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
