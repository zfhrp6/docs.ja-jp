---
title: ICLRStrongName::StrongNameSignatureVerificationFromImage メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60dbb8d8461015c791a70d6c2617b1c81e5ba17f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434269"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="b169a-102">ICLRStrongName::StrongNameSignatureVerificationFromImage メソッド</span><span class="sxs-lookup"><span data-stu-id="b169a-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="b169a-103">メモリに既にマップされているアセンブリが関連付けられている公開キーの有効なことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b169a-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b169a-104">構文</span><span class="sxs-lookup"><span data-stu-id="b169a-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b169a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b169a-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="b169a-106">[in]マップされているアセンブリ マニフェストの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="b169a-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="b169a-107">[in]マップされたイメージのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="b169a-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="b169a-108">[in]検証動作を制御するフラグ。</span><span class="sxs-lookup"><span data-stu-id="b169a-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="b169a-109">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b169a-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="b169a-110">`SN_INFLAG_FORCE_VER` (0x00000001) のレジストリ設定を上書きする必要がある場合でも強制的に検証します。</span><span class="sxs-lookup"><span data-stu-id="b169a-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="b169a-111">`SN_INFLAG_INSTALL` (0x00000002) - これが初めてこのイメージ上で実行する検証であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b169a-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="b169a-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) のキャッシュで管理者特権を持っているユーザーにのみアクセスを許可することを指定します。</span><span class="sxs-lookup"><span data-stu-id="b169a-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="b169a-113">`SN_INFLAG_USER_ACCESS` (0x00000008) のアセンブリが現在のユーザーのみアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b169a-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="b169a-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) のキャッシュはしないことを指定のアクセス制限を保証します。</span><span class="sxs-lookup"><span data-stu-id="b169a-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="b169a-115">`SN_INFLAG_RUNTIME` (0x80000000) - 内部デバッグのために予約されています。</span><span class="sxs-lookup"><span data-stu-id="b169a-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="b169a-116">[out]追加の出力情報に対するフラグです。</span><span class="sxs-lookup"><span data-stu-id="b169a-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="b169a-117">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b169a-117">The following value is supported:</span></span>  
  
-   <span data-ttu-id="b169a-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - この値は設定`false`レジストリ設定のために、検証が成功したことを指定します。</span><span class="sxs-lookup"><span data-stu-id="b169a-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b169a-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="b169a-119">Return Value</span></span>  
 <span data-ttu-id="b169a-120">`S_OK` メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="b169a-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b169a-121">要件</span><span class="sxs-lookup"><span data-stu-id="b169a-121">Requirements</span></span>  
 <span data-ttu-id="b169a-122">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b169a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b169a-123">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b169a-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b169a-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b169a-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b169a-125">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b169a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b169a-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="b169a-126">See Also</span></span>  
 [<span data-ttu-id="b169a-127">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b169a-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
