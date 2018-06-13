---
title: StrongNameKeyGenEx 関数
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e65e962d099e944fe243b3acc0a7c25a3bb960c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458671"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="b672b-102">StrongNameKeyGenEx 関数</span><span class="sxs-lookup"><span data-stu-id="b672b-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="b672b-103">厳密な名前に使用するため、指定されたキー サイズで新しい公開/秘密キー ペアを生成します。</span><span class="sxs-lookup"><span data-stu-id="b672b-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="b672b-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="b672b-104">This function has been deprecated.</span></span> <span data-ttu-id="b672b-105">使用して、 [iclrstrongname::strongnamekeygenex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="b672b-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b672b-106">構文</span><span class="sxs-lookup"><span data-stu-id="b672b-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b672b-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b672b-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="b672b-108">[in]要求されたキー コンテナーの名前です。</span><span class="sxs-lookup"><span data-stu-id="b672b-108">[in] The requested key container name.</span></span> <span data-ttu-id="b672b-109">`wszKeyContainer` 一時的な名前を生成する場合は null か空でない文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b672b-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b672b-110">[in]登録キーのままにするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b672b-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="b672b-111">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b672b-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="b672b-112">0x00000000 の際に使用される`wszKeyContainer`は一時的なキー コンテナー名を生成する場合は null です。</span><span class="sxs-lookup"><span data-stu-id="b672b-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="b672b-113">0x00000001 (`SN_LEAVE_KEY`)-キーを左に登録する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="b672b-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="b672b-114">[in]ビット単位のキーの要求されたサイズ。</span><span class="sxs-lookup"><span data-stu-id="b672b-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="b672b-115">[out]返された公開/秘密キー ペア。</span><span class="sxs-lookup"><span data-stu-id="b672b-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="b672b-116">[out]サイズをバイト単位での`ppbKeyBlob`します。</span><span class="sxs-lookup"><span data-stu-id="b672b-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b672b-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="b672b-117">Return Value</span></span>  
 <span data-ttu-id="b672b-118">`true` 正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="b672b-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b672b-119">コメント</span><span class="sxs-lookup"><span data-stu-id="b672b-119">Remarks</span></span>  
 <span data-ttu-id="b672b-120">.NET Framework のバージョン 1.0 および 1.1 が必要な`dwKeySize`厳密な名前でアセンブリに署名する 1024 ビットのバージョン 2.0 には、2048 ビットのキーのサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="b672b-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="b672b-121">呼び出す必要があります、キーが取得された後、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)割り当てられたメモリを解放する関数。</span><span class="sxs-lookup"><span data-stu-id="b672b-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="b672b-122">場合、`StrongNameKeyGenEx`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="b672b-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b672b-123">要件</span><span class="sxs-lookup"><span data-stu-id="b672b-123">Requirements</span></span>  
 <span data-ttu-id="b672b-124">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b672b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b672b-125">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="b672b-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b672b-126">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b672b-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b672b-127">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b672b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b672b-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="b672b-128">See Also</span></span>  
 [<span data-ttu-id="b672b-129">StrongNameKeyGenEx メソッド</span><span class="sxs-lookup"><span data-stu-id="b672b-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="b672b-130">StrongNameKeyGen メソッド</span><span class="sxs-lookup"><span data-stu-id="b672b-130">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="b672b-131">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b672b-131">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
