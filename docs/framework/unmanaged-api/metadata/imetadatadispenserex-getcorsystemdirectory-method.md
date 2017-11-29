---
title: "IMetaDataDispenserEx::GetCORSystemDirectory メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.GetCORSystemDirectory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a876d6ffb8331ee52789d5c146db7615d352dc1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="f1fff-102">IMetaDataDispenserEx::GetCORSystemDirectory メソッド</span><span class="sxs-lookup"><span data-stu-id="f1fff-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="f1fff-103">現在の共通言語ランタイム (CLR) を保持するディレクトリを取得します。</span><span class="sxs-lookup"><span data-stu-id="f1fff-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="f1fff-104">このメソッドは、アウト プロセスのデバッガーで使用するためだけサポートします。</span><span class="sxs-lookup"><span data-stu-id="f1fff-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="f1fff-105">別のコンポーネントから呼び出す場合、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="f1fff-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1fff-106">構文</span><span class="sxs-lookup"><span data-stu-id="f1fff-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1fff-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f1fff-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="f1fff-108">[out]ディレクトリ名を受け取るバッファー。</span><span class="sxs-lookup"><span data-stu-id="f1fff-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f1fff-109">[in]サイズをバイト単位での`szBuffer`します。</span><span class="sxs-lookup"><span data-stu-id="f1fff-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="f1fff-110">[out]実際に返されるバイト数`szBuffer`です。</span><span class="sxs-lookup"><span data-stu-id="f1fff-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1fff-111">要件</span><span class="sxs-lookup"><span data-stu-id="f1fff-111">Requirements</span></span>  
 <span data-ttu-id="f1fff-112">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f1fff-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1fff-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f1fff-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1fff-114">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="f1fff-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1fff-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1fff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1fff-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1fff-116">See Also</span></span>  
 [<span data-ttu-id="f1fff-117">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1fff-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="f1fff-118">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1fff-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
