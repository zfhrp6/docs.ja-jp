---
title: "ICLRStrongName::GetHashFromBlob メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: afb3614d4911b7e8b8666b1205af1c1d3d176b5d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="eb612-102">ICLRStrongName::GetHashFromBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="eb612-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="eb612-103">指定したハッシュ アルゴリズムを使用して、指定されたメモリ アドレスのアセンブリのハッシュを取得します。</span><span class="sxs-lookup"><span data-stu-id="eb612-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb612-104">構文</span><span class="sxs-lookup"><span data-stu-id="eb612-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb612-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eb612-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="eb612-106">[in]ハッシュされるメモリ ブロックのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eb612-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="eb612-107">[in]メモリ ブロックの長さ、(バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="eb612-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="eb612-108">[入力、出力].ハッシュ アルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="eb612-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="eb612-109">既定のアルゴリズムに 0 を使用します。</span><span class="sxs-lookup"><span data-stu-id="eb612-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="eb612-110">[out]返されるハッシュ バッファー。</span><span class="sxs-lookup"><span data-stu-id="eb612-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="eb612-111">[in]場合は、要求された最大サイズ`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="eb612-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="eb612-112">[out]サイズ (バイト単位)、返された`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="eb612-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eb612-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="eb612-113">Return Value</span></span>  
 <span data-ttu-id="eb612-114">`S_OK`メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="eb612-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb612-115">要件</span><span class="sxs-lookup"><span data-stu-id="eb612-115">Requirements</span></span>  
 <span data-ttu-id="eb612-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="eb612-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb612-117">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="eb612-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="eb612-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="eb612-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb612-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb612-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb612-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb612-120">See Also</span></span>  
 [<span data-ttu-id="eb612-121">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb612-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
