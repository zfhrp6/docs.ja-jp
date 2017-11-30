---
title: "ICLRStrongName::StrongNameSignatureGenerationEx メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureGenerationEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80b0527be680ed755366f77593e4dc7e1dea830c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="ae297-102">ICLRStrongName::StrongNameSignatureGenerationEx メソッド</span><span class="sxs-lookup"><span data-stu-id="ae297-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="ae297-103">指定したフラグに基づいて、指定したアセンブリの厳密な名前の署名を生成します。</span><span class="sxs-lookup"><span data-stu-id="ae297-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae297-104">構文</span><span class="sxs-lookup"><span data-stu-id="ae297-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae297-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ae297-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ae297-106">[in]厳密な名前の署名の生成対象となるアセンブリのマニフェストを格納しているファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="ae297-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="ae297-107">[in]公開/秘密キー ペアを格納するキー コンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="ae297-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="ae297-108">場合`pbKeyBlob`が null、`wszKeyContainer`暗号化サービス プロバイダー (CSP) 内で有効なコンテナーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae297-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="ae297-109">この場合、コンテナーに格納されているキーのペアは、ファイルの署名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ae297-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="ae297-110">場合`pbKeyBlob`が null でないと見なされますのキー ペア キー バイナリ ラージ オブジェクト (BLOB) に含まれています。</span><span class="sxs-lookup"><span data-stu-id="ae297-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ae297-111">[in]公開/秘密キー ペアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ae297-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="ae297-112">Win32 によって作成された形式では、このペア`CryptExportKey`関数。</span><span class="sxs-lookup"><span data-stu-id="ae297-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="ae297-113">場合`pbKeyBlob`は null、によって指定されたキー コンテナー`wszKeyContainer`キー ペアを格納すると見なされます。</span><span class="sxs-lookup"><span data-stu-id="ae297-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ae297-114">[in]サイズをバイト単位での`pbKeyBlob`します。</span><span class="sxs-lookup"><span data-stu-id="ae297-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="ae297-115">[out]共通言語ランタイムをするには、署名を返します場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ae297-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="ae297-116">場合`ppbSignatureBlob`が null の場合、ランタイム、署名ファイルに格納で指定された`wszFilePath`です。</span><span class="sxs-lookup"><span data-stu-id="ae297-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="ae297-117">場合`ppbSignatureBlob`が null でない、共通言語ランタイムは領域を割り当てますを返す、署名します。</span><span class="sxs-lookup"><span data-stu-id="ae297-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="ae297-118">呼び出し元が使用して、この領域を解放する必要があります、 [iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ae297-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="ae297-119">[out]返された署名のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="ae297-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ae297-120">[in]1 つ以上の次の値。</span><span class="sxs-lookup"><span data-stu-id="ae297-120">[in] One or more of the following values:</span></span>  
  
-   <span data-ttu-id="ae297-121">`SN_SIGN_ALL_FILES`(0x00000001) - リンクされたモジュールのすべてのハッシュを再計算します。</span><span class="sxs-lookup"><span data-stu-id="ae297-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
-   <span data-ttu-id="ae297-122">`SN_TEST_SIGN`(0x00000002) - テスト アセンブリに署名します。</span><span class="sxs-lookup"><span data-stu-id="ae297-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae297-123">戻り値</span><span class="sxs-lookup"><span data-stu-id="ae297-123">Return Value</span></span>  
 <span data-ttu-id="ae297-124">`S_OK`メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="ae297-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae297-125">コメント</span><span class="sxs-lookup"><span data-stu-id="ae297-125">Remarks</span></span>  
 <span data-ttu-id="ae297-126">Null を指定する`wszFilePath`署名を作成することがなく、署名のサイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="ae297-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="ae297-127">署名は、いずれか、ファイルに直接格納または呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="ae297-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="ae297-128">場合`SN_SIGN_ALL_FILES`が指定されているが、公開キーは含まれません (両方`pbKeyBlob`と`wszFilePath`が null)、リンクされたモジュールのハッシュが再計算されますが、アセンブリは、再署名することはありません。</span><span class="sxs-lookup"><span data-stu-id="ae297-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="ae297-129">場合`SN_TEST_SIGN`を指定すると、共通言語ランタイム ヘッダーは、アセンブリは厳密な名前で署名されていることを示すためには変更されません。</span><span class="sxs-lookup"><span data-stu-id="ae297-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae297-130">要件</span><span class="sxs-lookup"><span data-stu-id="ae297-130">Requirements</span></span>  
 <span data-ttu-id="ae297-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ae297-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae297-132">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ae297-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ae297-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ae297-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae297-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae297-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae297-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae297-135">See Also</span></span>  
 [<span data-ttu-id="ae297-136">StrongNameSignatureGeneration メソッド</span><span class="sxs-lookup"><span data-stu-id="ae297-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="ae297-137">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ae297-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
