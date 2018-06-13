---
title: ICLRStrongName::StrongNameSignatureGeneration メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 217b54a615d7c553e714ef87b3c2bb6a1919ae98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435376"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="7b11a-102">ICLRStrongName::StrongNameSignatureGeneration メソッド</span><span class="sxs-lookup"><span data-stu-id="7b11a-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="7b11a-103">指定したアセンブリの厳密な名前の署名を生成します。</span><span class="sxs-lookup"><span data-stu-id="7b11a-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b11a-104">構文</span><span class="sxs-lookup"><span data-stu-id="7b11a-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b11a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7b11a-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="7b11a-106">[in]厳密な名前の署名の生成対象となるアセンブリのマニフェストを格納しているファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="7b11a-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="7b11a-107">[in]公開/秘密キー ペアを格納するキー コンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="7b11a-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="7b11a-108">場合`pbKeyBlob`が null、`wszKeyContainer`暗号化サービス プロバイダー (CSP) 内で有効なコンテナーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b11a-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="7b11a-109">この場合、コンテナーに格納されているキーのペアは、ファイルの署名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7b11a-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="7b11a-110">場合`pbKeyBlob`が null でないと見なされますのキー ペア キー バイナリ ラージ オブジェクト (BLOB) に含まれています。</span><span class="sxs-lookup"><span data-stu-id="7b11a-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="7b11a-111">キーは、1024 ビットの Rivest-shamir-adleman (RSA) 署名キーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b11a-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="7b11a-112">この時点では、その他の種類のキーはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="7b11a-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="7b11a-113">[in]公開/秘密キー ペアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7b11a-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="7b11a-114">Win32 によって作成された形式では、このペア`CryptExportKey`関数。</span><span class="sxs-lookup"><span data-stu-id="7b11a-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="7b11a-115">場合`pbKeyBlob`は null、によって指定されたキー コンテナー`wszKeyContainer`キー ペアを格納すると見なされます。</span><span class="sxs-lookup"><span data-stu-id="7b11a-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="7b11a-116">[in]サイズをバイト単位での`pbKeyBlob`します。</span><span class="sxs-lookup"><span data-stu-id="7b11a-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="7b11a-117">[out]共通言語ランタイムをするには、署名を返します場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7b11a-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="7b11a-118">場合`ppbSignatureBlob`が null の場合、ランタイム、署名ファイルに格納で指定された`wszFilePath`です。</span><span class="sxs-lookup"><span data-stu-id="7b11a-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="7b11a-119">場合`ppbSignatureBlob`が null でない、共通言語ランタイムは領域を割り当てますを返す、署名します。</span><span class="sxs-lookup"><span data-stu-id="7b11a-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="7b11a-120">呼び出し元を使用してこの領域を解放する必要があります、 [iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="7b11a-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="7b11a-121">[out]返された署名のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="7b11a-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b11a-122">戻り値</span><span class="sxs-lookup"><span data-stu-id="7b11a-122">Return Value</span></span>  
 <span data-ttu-id="7b11a-123">`S_OK` メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="7b11a-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b11a-124">コメント</span><span class="sxs-lookup"><span data-stu-id="7b11a-124">Remarks</span></span>  
 <span data-ttu-id="7b11a-125">Null を指定する`wszFilePath`署名を作成することがなく、署名のサイズを計算します。</span><span class="sxs-lookup"><span data-stu-id="7b11a-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="7b11a-126">署名があることができます、ファイルに直接格納または呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="7b11a-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b11a-127">要件</span><span class="sxs-lookup"><span data-stu-id="7b11a-127">Requirements</span></span>  
 <span data-ttu-id="7b11a-128">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7b11a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b11a-129">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7b11a-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7b11a-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="7b11a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b11a-131">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b11a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b11a-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b11a-132">See Also</span></span>  
 [<span data-ttu-id="7b11a-133">StrongNameSignatureGenerationEx メソッド</span><span class="sxs-lookup"><span data-stu-id="7b11a-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [<span data-ttu-id="7b11a-134">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7b11a-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
