---
title: ICLRStrongName::GetHashFromFile メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94d17b6c8150744d4beca5e74827d235f81af08c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433316"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="3d9f7-102">ICLRStrongName::GetHashFromFile メソッド</span><span class="sxs-lookup"><span data-stu-id="3d9f7-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="3d9f7-103">指定されたファイルの内容のハッシュを生成します。</span><span class="sxs-lookup"><span data-stu-id="3d9f7-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d9f7-104">構文</span><span class="sxs-lookup"><span data-stu-id="3d9f7-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d9f7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3d9f7-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="3d9f7-106">[in]ハッシュには、ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="3d9f7-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="3d9f7-107">[入力、出力].ハッシュを生成するときに使用するアルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="3d9f7-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="3d9f7-108">有効なアルゴリズムを使用して、Win32 CryptoAPI で定義されています。</span><span class="sxs-lookup"><span data-stu-id="3d9f7-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="3d9f7-109">場合`piHashAlg`は 0、CALG_SHA 1 が使用される既定のアルゴリズムに設定します。</span><span class="sxs-lookup"><span data-stu-id="3d9f7-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="3d9f7-110">[out]生成されたハッシュを含むバイト配列。</span><span class="sxs-lookup"><span data-stu-id="3d9f7-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="3d9f7-111">[in]バッファーの最大サイズを`pbHash`を指します。</span><span class="sxs-lookup"><span data-stu-id="3d9f7-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="3d9f7-112">[out]サイズ (バイト単位)、返された`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="3d9f7-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d9f7-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="3d9f7-113">Return Value</span></span>  
 <span data-ttu-id="3d9f7-114">`S_OK` メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="3d9f7-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d9f7-115">コメント</span><span class="sxs-lookup"><span data-stu-id="3d9f7-115">Remarks</span></span>  
 <span data-ttu-id="3d9f7-116">このメソッドと同じ、 [iclrstrongname::gethashfromfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)メソッド、名前を指定する点を除いては Unicode ではなく ANSI です。</span><span class="sxs-lookup"><span data-stu-id="3d9f7-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d9f7-117">要件</span><span class="sxs-lookup"><span data-stu-id="3d9f7-117">Requirements</span></span>  
 <span data-ttu-id="3d9f7-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3d9f7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d9f7-119">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3d9f7-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3d9f7-120">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3d9f7-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d9f7-121">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d9f7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d9f7-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d9f7-122">See Also</span></span>  
 [<span data-ttu-id="3d9f7-123">GetHashFromFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="3d9f7-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="3d9f7-124">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d9f7-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
