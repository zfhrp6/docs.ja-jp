---
title: GetHashFromAssemblyFileW 関数
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 832d66eee14680870e70f1e0e8d40987eff3257f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457575"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="affad-102">GetHashFromAssemblyFileW 関数</span><span class="sxs-lookup"><span data-stu-id="affad-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="affad-103">指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュを取得します。</span><span class="sxs-lookup"><span data-stu-id="affad-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="affad-104">アセンブリ ファイルへのパスは、Unicode 文字列として指定してください。</span><span class="sxs-lookup"><span data-stu-id="affad-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="affad-105">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="affad-105">This function has been deprecated.</span></span> <span data-ttu-id="affad-106">使用して、 [iclrstrongname::gethashfromassemblyfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="affad-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="affad-107">構文</span><span class="sxs-lookup"><span data-stu-id="affad-107">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="affad-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="affad-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="affad-109">[in]ハッシュされるファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="affad-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="affad-110">このパラメーターは、Unicode 文字列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="affad-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="affad-111">[入力、出力].ハッシュ アルゴリズムを指定する定数。</span><span class="sxs-lookup"><span data-stu-id="affad-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="affad-112">0 を既定のハッシュ アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="affad-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="affad-113">[out]返されるハッシュ バッファー。</span><span class="sxs-lookup"><span data-stu-id="affad-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="affad-114">[in]場合は、要求された最大サイズ`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="affad-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="affad-115">[out]サイズをバイト単位で返される`pbHash`です。</span><span class="sxs-lookup"><span data-stu-id="affad-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="affad-116">要件</span><span class="sxs-lookup"><span data-stu-id="affad-116">Requirements</span></span>  
 <span data-ttu-id="affad-117">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="affad-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="affad-118">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="affad-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="affad-119">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="affad-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="affad-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="affad-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="affad-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="affad-121">See Also</span></span>  
 [<span data-ttu-id="affad-122">GetHashFromAssemblyFileW メソッド</span><span class="sxs-lookup"><span data-stu-id="affad-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="affad-123">GetHashFromAssemblyFile メソッド</span><span class="sxs-lookup"><span data-stu-id="affad-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="affad-124">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="affad-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
