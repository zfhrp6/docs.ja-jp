---
title: GetHashFromBlob 関数
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 427d93a9aff527d36720c4199782fa104a66f8d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="d0064-102">GetHashFromBlob 関数</span><span class="sxs-lookup"><span data-stu-id="d0064-102">GetHashFromBlob Function</span></span>
<span data-ttu-id="d0064-103">指定したハッシュ アルゴリズムを使用して、指定されたメモリ アドレスのアセンブリのハッシュを取得します。</span><span class="sxs-lookup"><span data-stu-id="d0064-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="d0064-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="d0064-104">This function has been deprecated.</span></span> <span data-ttu-id="d0064-105">使用して、 [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="d0064-105">Use the [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0064-106">構文</span><span class="sxs-lookup"><span data-stu-id="d0064-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="d0064-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d0064-107">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="d0064-108">[in]ハッシュされるメモリ ブロックのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d0064-108">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="d0064-109">[in]メモリ ブロックの長さ、(バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="d0064-109">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d0064-110">[入力、出力].ハッシュ アルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="d0064-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="d0064-111">既定のアルゴリズムに 0 を使用します。</span><span class="sxs-lookup"><span data-stu-id="d0064-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d0064-112">[out]返されるハッシュ バッファー。</span><span class="sxs-lookup"><span data-stu-id="d0064-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d0064-113">[in]場合は、要求された最大サイズ`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="d0064-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d0064-114">[out]サイズ (バイト単位)、返された`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="d0064-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0064-115">要件</span><span class="sxs-lookup"><span data-stu-id="d0064-115">Requirements</span></span>  
 <span data-ttu-id="d0064-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d0064-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0064-117">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d0064-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d0064-118">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d0064-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d0064-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0064-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0064-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0064-120">See Also</span></span>  
 [<span data-ttu-id="d0064-121">GetHashFromBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="d0064-121">GetHashFromBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)  
 [<span data-ttu-id="d0064-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0064-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
