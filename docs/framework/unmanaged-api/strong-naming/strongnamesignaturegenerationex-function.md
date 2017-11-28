---
title: "StrongNameSignatureGenerationEx 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureGenerationEx
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureGenerationEx
helpviewer_keywords: StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 49000a00f278b4c1dd7a2eeded7eb91a592c863f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="b784a-102">StrongNameSignatureGenerationEx 関数</span><span class="sxs-lookup"><span data-stu-id="b784a-102">StrongNameSignatureGenerationEx Function</span></span>
<span data-ttu-id="b784a-103">指定したフラグに基づいて、指定したアセンブリの厳密な名前の署名を生成します。</span><span class="sxs-lookup"><span data-stu-id="b784a-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="b784a-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="b784a-104">This function has been deprecated.</span></span> <span data-ttu-id="b784a-105">使用して、 [iclrstrongname::strongnamesignaturegenerationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="b784a-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b784a-106">構文</span><span class="sxs-lookup"><span data-stu-id="b784a-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b784a-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b784a-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b784a-108">[in]厳密な名前の署名の生成対象となるアセンブリのマニフェストを格納しているファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="b784a-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="b784a-109">[in]公開/秘密キー ペアを格納するキー コンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="b784a-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="b784a-110">場合`pbKeyBlob`が null、`wszKeyContainer`暗号化サービス プロバイダー (CSP) 内で有効なコンテナーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b784a-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="b784a-111">この場合、コンテナーに格納されているキーのペアは、ファイルの署名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b784a-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="b784a-112">場合`pbKeyBlob`が null でないと見なされますのキー ペア キー バイナリ ラージ オブジェクト (BLOB) に含まれています。</span><span class="sxs-lookup"><span data-stu-id="b784a-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="b784a-113">[in]公開/秘密キー ペアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b784a-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="b784a-114">Win32 によって作成された形式では、このペア`CryptExportKey`関数。</span><span class="sxs-lookup"><span data-stu-id="b784a-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="b784a-115">場合`pbKeyBlob`は null、によって指定されたキー コンテナー`wszKeyContainer`キー ペアを格納すると見なされます。</span><span class="sxs-lookup"><span data-stu-id="b784a-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="b784a-116">[in]サイズをバイト単位での`pbKeyBlob`します。</span><span class="sxs-lookup"><span data-stu-id="b784a-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="b784a-117">[out]共通言語ランタイムをするには、署名を返します場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b784a-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="b784a-118">場合`ppbSignatureBlob`が null の場合、ランタイム、署名ファイルに格納で指定された`wszFilePath`です。</span><span class="sxs-lookup"><span data-stu-id="b784a-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="b784a-119">場合`ppbSignatureBlob`が null でない、共通言語ランタイムは領域を割り当てますを返す、署名します。</span><span class="sxs-lookup"><span data-stu-id="b784a-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="b784a-120">呼び出し元が使用して、この領域を解放する必要があります、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="b784a-120">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="b784a-121">[out]返された署名のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="b784a-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b784a-122">[in]1 つ以上の次の値。</span><span class="sxs-lookup"><span data-stu-id="b784a-122">[in] One or more of the following values:</span></span>  
  
-   <span data-ttu-id="b784a-123">`SN_SIGN_ALL_FILES`(0x00000001) - リンクされたモジュールのすべてのハッシュを再計算します。</span><span class="sxs-lookup"><span data-stu-id="b784a-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
-   <span data-ttu-id="b784a-124">`SN_TEST_SIGN`(0x00000002) - テスト アセンブリに署名します。</span><span class="sxs-lookup"><span data-stu-id="b784a-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b784a-125">戻り値</span><span class="sxs-lookup"><span data-stu-id="b784a-125">Return Value</span></span>  
 <span data-ttu-id="b784a-126">`true`正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="b784a-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b784a-127">コメント</span><span class="sxs-lookup"><span data-stu-id="b784a-127">Remarks</span></span>  
 <span data-ttu-id="b784a-128">Null を指定する`wszFilePath`署名を作成することがなく、署名のサイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="b784a-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="b784a-129">署名は、いずれか、ファイルに直接格納または呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="b784a-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="b784a-130">場合`SN_SIGN_ALL_FILES`が指定されているが、公開キーは含まれません (両方`pbKeyBlob`と`wszFilePath`が null)、リンクされたモジュールのハッシュが再計算されますが、アセンブリは、再署名することはありません。</span><span class="sxs-lookup"><span data-stu-id="b784a-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="b784a-131">場合`SN_TEST_SIGN`を指定すると、共通言語ランタイム ヘッダーは、アセンブリは厳密な名前で署名されていることを示すためには変更されません。</span><span class="sxs-lookup"><span data-stu-id="b784a-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="b784a-132">場合、`StrongNameSignatureGenerationEx`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="b784a-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b784a-133">要件</span><span class="sxs-lookup"><span data-stu-id="b784a-133">Requirements</span></span>  
 <span data-ttu-id="b784a-134">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b784a-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b784a-135">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="b784a-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b784a-136">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b784a-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b784a-137">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b784a-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b784a-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="b784a-138">See Also</span></span>  
 [<span data-ttu-id="b784a-139">StrongNameSignatureGenerationEx メソッド</span><span class="sxs-lookup"><span data-stu-id="b784a-139">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [<span data-ttu-id="b784a-140">StrongNameSignatureGeneration メソッド</span><span class="sxs-lookup"><span data-stu-id="b784a-140">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="b784a-141">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b784a-141">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
