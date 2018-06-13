---
title: StrongNameGetPublicKey 関数
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3ace4a3103231f776d4e2b034f8e18ce861ee97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461014"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="30806-102">StrongNameGetPublicKey 関数</span><span class="sxs-lookup"><span data-stu-id="30806-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="30806-103">プライベート/パブリック キーのペアから公開キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="30806-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="30806-104">暗号化サービス プロバイダー (CSP) 内のキー コンテナー名、またはバイトの生のコレクションとして、キーのペアを指定できます。</span><span class="sxs-lookup"><span data-stu-id="30806-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="30806-105">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="30806-105">This function has been deprecated.</span></span> <span data-ttu-id="30806-106">使用して、 [iclrstrongname::strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="30806-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30806-107">構文</span><span class="sxs-lookup"><span data-stu-id="30806-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30806-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="30806-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="30806-109">[in]公開/秘密キー ペアを格納するキー コンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="30806-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="30806-110">場合`pbKeyBlob`が null、 `szKeyContainer` CSP 内の有効なコンテナーを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="30806-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="30806-111">この場合、`StrongNameGetPublicKey`コンテナーに格納されているキーのペアから公開キーを抽出します。</span><span class="sxs-lookup"><span data-stu-id="30806-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="30806-112">場合`pbKeyBlob`が null でないと見なされますのキー ペア キー バイナリ ラージ オブジェクト (BLOB) に含まれています。</span><span class="sxs-lookup"><span data-stu-id="30806-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="30806-113">キーは、1024 ビットの Rivest-shamir-adleman (RSA) 署名キーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="30806-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="30806-114">この時点では、その他の種類のキーはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="30806-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="30806-115">[in]公開/秘密キー ペアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="30806-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="30806-116">Win32 によって作成された形式では、このペア`CryptExportKey`関数。</span><span class="sxs-lookup"><span data-stu-id="30806-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="30806-117">場合`pbKeyBlob`は null、によって指定されたキー コンテナー`szKeyContainer`キー ペアを格納すると見なされます。</span><span class="sxs-lookup"><span data-stu-id="30806-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="30806-118">[in]サイズをバイト単位での`pbKeyBlob`します。</span><span class="sxs-lookup"><span data-stu-id="30806-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="30806-119">[out]返される公開キー BLOB。</span><span class="sxs-lookup"><span data-stu-id="30806-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="30806-120">`ppbPublicKeyBlob`パラメーターが、共通言語ランタイムによって割り当てられるし、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="30806-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="30806-121">呼び出し元を使用して、メモリを解放する必要があります、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="30806-121">The caller must free the memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="30806-122">[out]返される公開キー BLOB のサイズ。</span><span class="sxs-lookup"><span data-stu-id="30806-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30806-123">戻り値</span><span class="sxs-lookup"><span data-stu-id="30806-123">Return Value</span></span>  
 <span data-ttu-id="30806-124">`true` 正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="30806-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30806-125">コメント</span><span class="sxs-lookup"><span data-stu-id="30806-125">Remarks</span></span>  
 <span data-ttu-id="30806-126">公開キーが含まれている、 [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="30806-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="30806-127">場合、`StrongNameGetPublicKey`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="30806-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30806-128">要件</span><span class="sxs-lookup"><span data-stu-id="30806-128">Requirements</span></span>  
 <span data-ttu-id="30806-129">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="30806-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30806-130">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="30806-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="30806-131">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="30806-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30806-132">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30806-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30806-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="30806-133">See Also</span></span>  
 [<span data-ttu-id="30806-134">StrongNameGetPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="30806-134">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="30806-135">StrongNameTokenFromPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="30806-135">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="30806-136">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30806-136">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [<span data-ttu-id="30806-137">PublicKeyBlob 構造体</span><span class="sxs-lookup"><span data-stu-id="30806-137">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
