---
title: ICLRStrongName::StrongNameKeyInstall メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 572afc5eb9ec3cf52199e5ad74406c876485461c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="84ddf-102">ICLRStrongName::StrongNameKeyInstall メソッド</span><span class="sxs-lookup"><span data-stu-id="84ddf-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="84ddf-103">公開/秘密キー ペアをコンテナーにインポートします。</span><span class="sxs-lookup"><span data-stu-id="84ddf-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84ddf-104">構文</span><span class="sxs-lookup"><span data-stu-id="84ddf-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84ddf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="84ddf-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="84ddf-106">[in]キー コンテナーの名前。</span><span class="sxs-lookup"><span data-stu-id="84ddf-106">[in] The name of the key container.</span></span> <span data-ttu-id="84ddf-107">`wszKeyContainer` 空でない文字列にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="84ddf-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="84ddf-108">[in]バイナリのキーのペア。</span><span class="sxs-lookup"><span data-stu-id="84ddf-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="84ddf-109">[in]サイズをバイト単位での`pbKeyBlob`します。</span><span class="sxs-lookup"><span data-stu-id="84ddf-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84ddf-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="84ddf-110">Return Value</span></span>  
 <span data-ttu-id="84ddf-111">`S_OK` メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="84ddf-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84ddf-112">コメント</span><span class="sxs-lookup"><span data-stu-id="84ddf-112">Remarks</span></span>  
 <span data-ttu-id="84ddf-113">使用して、 [iclrstrongname::strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)メソッドは、キー コンテナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="84ddf-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84ddf-114">要件</span><span class="sxs-lookup"><span data-stu-id="84ddf-114">Requirements</span></span>  
 <span data-ttu-id="84ddf-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="84ddf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84ddf-116">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="84ddf-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="84ddf-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="84ddf-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84ddf-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84ddf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ddf-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="84ddf-119">See Also</span></span>  
 [<span data-ttu-id="84ddf-120">StrongNameKeyDelete メソッド</span><span class="sxs-lookup"><span data-stu-id="84ddf-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="84ddf-121">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="84ddf-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
