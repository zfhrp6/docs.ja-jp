---
title: ICLRStrongName::StrongNameKeyGen メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55b4fbb8785f788c9eb34f32b5078201f8253066
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433329"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="d11c4-102">ICLRStrongName::StrongNameKeyGen メソッド</span><span class="sxs-lookup"><span data-stu-id="d11c4-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="d11c4-103">厳密な名前に使用するために新しい公開/秘密キー ペアを作成します。</span><span class="sxs-lookup"><span data-stu-id="d11c4-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d11c4-104">構文</span><span class="sxs-lookup"><span data-stu-id="d11c4-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d11c4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d11c4-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="d11c4-106">[in]要求されたキー コンテナーの名前です。</span><span class="sxs-lookup"><span data-stu-id="d11c4-106">[in] The requested key container name.</span></span> <span data-ttu-id="d11c4-107">`wszKeyContainer` 空でない文字列または一時的な名前を生成するのには null でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="d11c4-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d11c4-108">[in]登録キーのままにするかどうかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="d11c4-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="d11c4-109">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d11c4-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="d11c4-110">0x00000000 の際に使用される`wszKeyContainer`は一時的なキー コンテナー名を生成する場合は null です。</span><span class="sxs-lookup"><span data-stu-id="d11c4-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="d11c4-111">0x00000001 (`SN_LEAVE_KEY`)-キーを左に登録する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="d11c4-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="d11c4-112">[out]返された公開/秘密キー ペア。</span><span class="sxs-lookup"><span data-stu-id="d11c4-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="d11c4-113">[out]サイズをバイト単位での`ppbKeyBlob`します。</span><span class="sxs-lookup"><span data-stu-id="d11c4-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d11c4-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="d11c4-114">Return Value</span></span>  
 <span data-ttu-id="d11c4-115">`S_OK` メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="d11c4-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d11c4-116">コメント</span><span class="sxs-lookup"><span data-stu-id="d11c4-116">Remarks</span></span>  
 <span data-ttu-id="d11c4-117">[Iclrstrongname::strongnamekeygen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)メソッドは、1024 ビット キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d11c4-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="d11c4-118">呼び出す必要があります、キーが取得された後、 [iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)を割り当てられたメモリを解放するメソッド。</span><span class="sxs-lookup"><span data-stu-id="d11c4-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d11c4-119">要件</span><span class="sxs-lookup"><span data-stu-id="d11c4-119">Requirements</span></span>  
 <span data-ttu-id="d11c4-120">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d11c4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d11c4-121">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d11c4-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d11c4-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d11c4-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d11c4-123">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d11c4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d11c4-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="d11c4-124">See Also</span></span>  
 [<span data-ttu-id="d11c4-125">StrongNameKeyGenEx メソッド</span><span class="sxs-lookup"><span data-stu-id="d11c4-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="d11c4-126">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d11c4-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
