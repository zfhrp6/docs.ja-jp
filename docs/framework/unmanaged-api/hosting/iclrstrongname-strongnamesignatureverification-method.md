---
title: "ICLRStrongName::StrongNameSignatureVerification メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureVerification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e326eadcf91fbab0edb81844172bfabbd0851dc7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="b17e9-102">ICLRStrongName::StrongNameSignatureVerification メソッド</span><span class="sxs-lookup"><span data-stu-id="b17e9-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="b17e9-103">指定されたパスにあるアセンブリ マニフェストが指定したフラグに従って検証される厳密な名前の署名を含むかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b17e9-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b17e9-104">構文</span><span class="sxs-lookup"><span data-stu-id="b17e9-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b17e9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b17e9-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b17e9-106">[in]確認するアセンブリのポータブル実行可能ファイル (.dll または .exe) ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="b17e9-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="b17e9-107">[in]検証動作を変更するフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="b17e9-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="b17e9-108">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b17e9-108">The following values are supported:</span></span>  
  
-   <span data-ttu-id="b17e9-109">`SN_INFLAG_FORCE_VER`(0x00000001) のレジストリ設定を上書きする必要がある場合でも強制的に検証します。</span><span class="sxs-lookup"><span data-stu-id="b17e9-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="b17e9-110">`SN_INFLAG_INSTALL`(0x00000002) - これが初めてマニフェストの検証であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b17e9-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   <span data-ttu-id="b17e9-111">`SN_INFLAG_ADMIN_ACCESS`(0x00000004) のキャッシュで管理者特権を持っているユーザーにのみアクセスを許可することを指定します。</span><span class="sxs-lookup"><span data-stu-id="b17e9-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="b17e9-112">`SN_INFLAG_USER_ACCESS`(0x00000008) のアセンブリが現在のユーザーのみアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b17e9-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="b17e9-113">`SN_INFLAG_ALL_ACCESS`(0x00000010) のキャッシュはしないことを指定のアクセス制限を保証します。</span><span class="sxs-lookup"><span data-stu-id="b17e9-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="b17e9-114">`SN_INFLAG_RUNTIME`(0x80000000) - 内部デバッグのために予約されています。</span><span class="sxs-lookup"><span data-stu-id="b17e9-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="b17e9-115">[out]厳密な名前の署名が検証されたかどうかを示すフラグです。</span><span class="sxs-lookup"><span data-stu-id="b17e9-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="b17e9-116">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b17e9-116">The following value is supported:</span></span>  
  
-   <span data-ttu-id="b17e9-117">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) - この値は設定`false`レジストリ設定のために、検証が成功したことを指定します。</span><span class="sxs-lookup"><span data-stu-id="b17e9-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b17e9-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="b17e9-118">Return Value</span></span>  
 <span data-ttu-id="b17e9-119">`S_OK`メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="b17e9-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b17e9-120">要件</span><span class="sxs-lookup"><span data-stu-id="b17e9-120">Requirements</span></span>  
 <span data-ttu-id="b17e9-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b17e9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b17e9-122">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b17e9-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b17e9-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b17e9-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b17e9-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b17e9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b17e9-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="b17e9-125">See Also</span></span>  
 [<span data-ttu-id="b17e9-126">StrongNameSignatureVerificationEx メソッド</span><span class="sxs-lookup"><span data-stu-id="b17e9-126">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="b17e9-127">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b17e9-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
