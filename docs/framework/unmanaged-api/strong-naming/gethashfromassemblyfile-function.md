---
title: "GetHashFromAssemblyFile 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromAssemblyFile
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromAssemblyFile
helpviewer_keywords: GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1598e4e332525f87392ae5b0ad486a735e760651
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="c65f1-102">GetHashFromAssemblyFile 関数</span><span class="sxs-lookup"><span data-stu-id="c65f1-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="c65f1-103">指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュを取得します。</span><span class="sxs-lookup"><span data-stu-id="c65f1-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="c65f1-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="c65f1-104">This function has been deprecated.</span></span> <span data-ttu-id="c65f1-105">使用して、 [iclrstrongname::gethashfromassemblyfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="c65f1-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c65f1-106">構文</span><span class="sxs-lookup"><span data-stu-id="c65f1-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c65f1-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c65f1-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="c65f1-108">[in]ハッシュされるファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="c65f1-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c65f1-109">[入力、出力].ハッシュ アルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="c65f1-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="c65f1-110">0 を既定のハッシュ アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="c65f1-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c65f1-111">[out]返されるハッシュ バッファー。</span><span class="sxs-lookup"><span data-stu-id="c65f1-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c65f1-112">[in]場合は、要求された最大サイズ`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="c65f1-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c65f1-113">[out]サイズをバイト単位で返される`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="c65f1-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c65f1-114">要件</span><span class="sxs-lookup"><span data-stu-id="c65f1-114">Requirements</span></span>  
 <span data-ttu-id="c65f1-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c65f1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c65f1-116">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c65f1-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c65f1-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="c65f1-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c65f1-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c65f1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c65f1-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c65f1-119">See Also</span></span>  
 [<span data-ttu-id="c65f1-120">GetHashFromAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="c65f1-120">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="c65f1-121">GetHashFromAssemblyFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="c65f1-121">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="c65f1-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c65f1-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
