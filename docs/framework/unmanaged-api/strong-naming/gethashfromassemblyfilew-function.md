---
title: "GetHashFromAssemblyFileW 関数"
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
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 938d7b5633a73aafb81b16fd2fa207160cac4e05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="91289-102">GetHashFromAssemblyFileW 関数</span><span class="sxs-lookup"><span data-stu-id="91289-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="91289-103">指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュを取得します。</span><span class="sxs-lookup"><span data-stu-id="91289-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="91289-104">アセンブリ ファイルへのパスは、Unicode 文字列として指定してください。</span><span class="sxs-lookup"><span data-stu-id="91289-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="91289-105">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="91289-105">This function has been deprecated.</span></span> <span data-ttu-id="91289-106">使用して、 [iclrstrongname::gethashfromassemblyfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="91289-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91289-107">構文</span><span class="sxs-lookup"><span data-stu-id="91289-107">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91289-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="91289-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="91289-109">[in]ハッシュされるファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="91289-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="91289-110">このパラメーターは、Unicode 文字列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91289-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="91289-111">[入力、出力].ハッシュ アルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="91289-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="91289-112">0 を既定のハッシュ アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="91289-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="91289-113">[out]返されるハッシュ バッファー。</span><span class="sxs-lookup"><span data-stu-id="91289-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="91289-114">[in]場合は、要求された最大サイズ`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="91289-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="91289-115">[out]サイズをバイト単位で返される`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="91289-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91289-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="91289-116">Requirements</span></span>  
 <span data-ttu-id="91289-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="91289-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91289-118">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="91289-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="91289-119">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="91289-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="91289-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91289-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91289-121">参照</span><span class="sxs-lookup"><span data-stu-id="91289-121">See Also</span></span>  
 [<span data-ttu-id="91289-122">GetHashFromAssemblyFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="91289-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="91289-123">GetHashFromAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="91289-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="91289-124">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="91289-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
