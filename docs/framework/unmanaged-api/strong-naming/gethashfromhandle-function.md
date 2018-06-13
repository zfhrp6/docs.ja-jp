---
title: GetHashFromHandle 関数
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30aad6fc62c8fee7448163ca69117b804203d505
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456483"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="99b75-102">GetHashFromHandle 関数</span><span class="sxs-lookup"><span data-stu-id="99b75-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="99b75-103">指定したハッシュ アルゴリズムを使用して、指定したファイル ハンドルを持つファイルの内容のハッシュを生成します。</span><span class="sxs-lookup"><span data-stu-id="99b75-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="99b75-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="99b75-104">This function has been deprecated.</span></span> <span data-ttu-id="99b75-105">使用して、 [iclrstrongname::gethashfromhandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="99b75-105">Use the [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99b75-106">構文</span><span class="sxs-lookup"><span data-stu-id="99b75-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99b75-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="99b75-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="99b75-108">[in]ハッシュされるファイルのハンドル。</span><span class="sxs-lookup"><span data-stu-id="99b75-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="99b75-109">[入力、出力].ハッシュ アルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="99b75-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="99b75-110">既定のアルゴリズムに 0 を使用します。</span><span class="sxs-lookup"><span data-stu-id="99b75-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="99b75-111">[out]返されるハッシュ バッファー。</span><span class="sxs-lookup"><span data-stu-id="99b75-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="99b75-112">[in]場合は、要求された最大サイズ`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="99b75-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="99b75-113">[out]サイズ (バイト単位)、返された`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="99b75-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99b75-114">要件</span><span class="sxs-lookup"><span data-stu-id="99b75-114">Requirements</span></span>  
 <span data-ttu-id="99b75-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="99b75-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99b75-116">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="99b75-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="99b75-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="99b75-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="99b75-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99b75-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b75-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="99b75-119">See Also</span></span>  
 [<span data-ttu-id="99b75-120">GetHashFromHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="99b75-120">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)  
 [<span data-ttu-id="99b75-121">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99b75-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
