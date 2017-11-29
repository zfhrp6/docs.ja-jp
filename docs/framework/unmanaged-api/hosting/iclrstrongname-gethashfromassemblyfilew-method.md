---
title: "ICLRStrongName::GetHashFromAssemblyFileW メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromAssemblyFileW
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 14b4e6dae97777873f458018acdaf0c3f5d4f070
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="a0481-102">ICLRStrongName::GetHashFromAssemblyFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="a0481-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="a0481-103">Unicode 文字列で指定されたファイルの内容のハッシュを生成します。</span><span class="sxs-lookup"><span data-stu-id="a0481-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0481-104">構文</span><span class="sxs-lookup"><span data-stu-id="a0481-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0481-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0481-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="a0481-106">[in]ハッシュされるファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="a0481-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="a0481-107">このパラメーターは、Unicode 文字列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0481-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="a0481-108">[入力、出力].ハッシュ アルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="a0481-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="a0481-109">0 を既定のハッシュ アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0481-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="a0481-110">[out]返されるハッシュ バッファー。</span><span class="sxs-lookup"><span data-stu-id="a0481-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="a0481-111">[in]場合は、要求された最大サイズ`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="a0481-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="a0481-112">[out]サイズをバイト単位で返される`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="a0481-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0481-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="a0481-113">Return Value</span></span>  
 <span data-ttu-id="a0481-114">`S_OK`メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="a0481-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0481-115">要件</span><span class="sxs-lookup"><span data-stu-id="a0481-115">Requirements</span></span>  
 <span data-ttu-id="a0481-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a0481-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0481-117">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a0481-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a0481-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0481-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0481-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0481-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0481-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0481-120">See Also</span></span>  
 [<span data-ttu-id="a0481-121">GetHashFromAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="a0481-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="a0481-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0481-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
