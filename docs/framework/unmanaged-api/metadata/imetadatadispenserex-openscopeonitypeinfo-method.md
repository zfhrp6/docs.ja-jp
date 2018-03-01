---
title: "IMetaDataDispenserEx::OpenScopeOnITypeInfo メソッド"
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
- IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 45c65d0194ed44122a87dcd000359187fc020d0e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="24ec4-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="24ec4-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="24ec4-103">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="24ec4-103">This method is not implemented.</span></span> <span data-ttu-id="24ec4-104">呼び出された場合、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="24ec4-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24ec4-105">構文</span><span class="sxs-lookup"><span data-stu-id="24ec4-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24ec4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="24ec4-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="24ec4-107">[in]ポインター、 [ITypeInfo](http://msdn.microsoft.com/library/f3356463-3373-4279-bae1-953378aa2680)を開くには、スコープの種類の情報を提供するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="24ec4-107">[in] Pointer to an [ITypeInfo](http://msdn.microsoft.com/library/f3356463-3373-4279-bae1-953378aa2680) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="24ec4-108">[in]オープン モードのフラグです。</span><span class="sxs-lookup"><span data-stu-id="24ec4-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="24ec4-109">[in]必要なインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="24ec4-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="24ec4-110">[out]返されたインターフェイスへのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="24ec4-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24ec4-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="24ec4-111">Requirements</span></span>  
 <span data-ttu-id="24ec4-112">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="24ec4-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24ec4-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="24ec4-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="24ec4-114">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="24ec4-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="24ec4-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24ec4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24ec4-116">参照</span><span class="sxs-lookup"><span data-stu-id="24ec4-116">See Also</span></span>  
 [<span data-ttu-id="24ec4-117">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="24ec4-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="24ec4-118">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="24ec4-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
