---
title: "ICLRStrongName::GetHashFromAssemblyFile メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6dcb0ca16c2ffdd8a928cec9cca44b628de34885
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="5112c-102">ICLRStrongName::GetHashFromAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="5112c-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="5112c-103">指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュを取得します。</span><span class="sxs-lookup"><span data-stu-id="5112c-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5112c-104">構文</span><span class="sxs-lookup"><span data-stu-id="5112c-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5112c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5112c-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="5112c-106">[in]ハッシュされるファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="5112c-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="5112c-107">[入力、出力].ハッシュ アルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="5112c-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="5112c-108">0 を既定のハッシュ アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="5112c-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="5112c-109">[out]返されるハッシュ バッファー。</span><span class="sxs-lookup"><span data-stu-id="5112c-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="5112c-110">[in]場合は、要求された最大サイズ`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="5112c-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="5112c-111">[out]サイズをバイト単位で返される`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="5112c-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5112c-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="5112c-112">Return Value</span></span>  
 <span data-ttu-id="5112c-113">`S_OK`メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="5112c-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5112c-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="5112c-114">Requirements</span></span>  
 <span data-ttu-id="5112c-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5112c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5112c-116">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5112c-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5112c-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5112c-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5112c-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5112c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5112c-119">参照</span><span class="sxs-lookup"><span data-stu-id="5112c-119">See Also</span></span>  
 [<span data-ttu-id="5112c-120">GetHashFromAssemblyFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="5112c-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="5112c-121">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5112c-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
