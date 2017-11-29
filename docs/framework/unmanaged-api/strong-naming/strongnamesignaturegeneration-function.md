---
title: "StrongNameSignatureGeneration 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureGeneration
helpviewer_keywords: StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26900b73e4c0b8b7501a59c3706966df5cf46120
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="dcc73-102">StrongNameSignatureGeneration 関数</span><span class="sxs-lookup"><span data-stu-id="dcc73-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="dcc73-103">指定したアセンブリの厳密な名前の署名を生成します。</span><span class="sxs-lookup"><span data-stu-id="dcc73-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="dcc73-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="dcc73-104">This function has been deprecated.</span></span> <span data-ttu-id="dcc73-105">使用して、 [iclrstrongname::strongnamesignaturegeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="dcc73-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcc73-106">構文</span><span class="sxs-lookup"><span data-stu-id="dcc73-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcc73-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dcc73-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="dcc73-108">[in]厳密な名前の署名の生成対象となるアセンブリのマニフェストを格納しているファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="dcc73-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="dcc73-109">[in]公開/秘密キー ペアを格納するキー コンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="dcc73-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="dcc73-110">場合`pbKeyBlob`が null、`wszKeyContainer`暗号化サービス プロバイダー (CSP) 内で有効なコンテナーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dcc73-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="dcc73-111">この場合、コンテナーに格納されているキーのペアは、ファイルの署名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="dcc73-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="dcc73-112">場合`pbKeyBlob`が null でないと見なされますのキー ペア キー バイナリ ラージ オブジェクト (BLOB) に含まれています。</span><span class="sxs-lookup"><span data-stu-id="dcc73-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="dcc73-113">キーは、1024 ビットの Rivest-shamir-adleman (RSA) 署名キーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="dcc73-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="dcc73-114">この時点では、その他の種類のキーはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="dcc73-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="dcc73-115">[in]公開/秘密キー ペアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dcc73-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="dcc73-116">Win32 によって作成された形式では、このペア`CryptExportKey`関数。</span><span class="sxs-lookup"><span data-stu-id="dcc73-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="dcc73-117">場合`pbKeyBlob`は null、によって指定されたキー コンテナー`wszKeyContainer`キー ペアを格納すると見なされます。</span><span class="sxs-lookup"><span data-stu-id="dcc73-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="dcc73-118">[in]サイズをバイト単位での`pbKeyBlob`します。</span><span class="sxs-lookup"><span data-stu-id="dcc73-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="dcc73-119">[out]共通言語ランタイムをするには、署名を返します場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="dcc73-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="dcc73-120">場合`ppbSignatureBlob`が null の場合、ランタイム、署名ファイルに格納で指定された`wszFilePath`です。</span><span class="sxs-lookup"><span data-stu-id="dcc73-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="dcc73-121">場合`ppbSignatureBlob`が null でない、共通言語ランタイムは領域を割り当てますを返す、署名します。</span><span class="sxs-lookup"><span data-stu-id="dcc73-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="dcc73-122">呼び出し元が使用して、この領域を解放する必要があります、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="dcc73-122">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="dcc73-123">[out]返された署名のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="dcc73-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dcc73-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="dcc73-124">Return Value</span></span>  
 <span data-ttu-id="dcc73-125">`true`正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="dcc73-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcc73-126">コメント</span><span class="sxs-lookup"><span data-stu-id="dcc73-126">Remarks</span></span>  
 <span data-ttu-id="dcc73-127">Null を指定する`wszFilePath`署名を作成することがなく、署名のサイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="dcc73-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="dcc73-128">署名があることができます、ファイルに直接格納または呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="dcc73-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="dcc73-129">場合、`StrongNameSignatureGeneration`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="dcc73-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcc73-130">要件</span><span class="sxs-lookup"><span data-stu-id="dcc73-130">Requirements</span></span>  
 <span data-ttu-id="dcc73-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dcc73-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcc73-132">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="dcc73-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="dcc73-133">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="dcc73-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dcc73-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcc73-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc73-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcc73-135">See Also</span></span>  
 [<span data-ttu-id="dcc73-136">StrongNameSignatureGeneration メソッド</span><span class="sxs-lookup"><span data-stu-id="dcc73-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="dcc73-137">StrongNameSignatureGenerationEx メソッド</span><span class="sxs-lookup"><span data-stu-id="dcc73-137">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [<span data-ttu-id="dcc73-138">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dcc73-138">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
