---
title: "IMetaDataImport::EnumUnresolvedMethods メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumUnresolvedMethods
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3c7709180e5b7811379c25977f8a8d23b91adb3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="74a1f-102">IMetaDataImport::EnumUnresolvedMethods メソッド</span><span class="sxs-lookup"><span data-stu-id="74a1f-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="74a1f-103">現在のメタデータ スコープ内の未解決のメソッドを表す MemberDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="74a1f-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74a1f-104">構文</span><span class="sxs-lookup"><span data-stu-id="74a1f-104">Syntax</span></span>  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74a1f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="74a1f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="74a1f-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="74a1f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="74a1f-107">このメソッドの最初の呼び出しで NULL があります。</span><span class="sxs-lookup"><span data-stu-id="74a1f-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="74a1f-108">[out]MemberDef トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="74a1f-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="74a1f-109">[in] `rMethods` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="74a1f-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="74a1f-110">[out]返される MemberDef トークン数`rMethods`です。</span><span class="sxs-lookup"><span data-stu-id="74a1f-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74a1f-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="74a1f-111">Return Value</span></span>  
  
|<span data-ttu-id="74a1f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74a1f-112">HRESULT</span></span>|<span data-ttu-id="74a1f-113">説明</span><span class="sxs-lookup"><span data-stu-id="74a1f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="74a1f-114">`EnumUnresolvedMethods`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="74a1f-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="74a1f-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="74a1f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="74a1f-116">その場合は、`pcTokens`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="74a1f-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74a1f-117">コメント</span><span class="sxs-lookup"><span data-stu-id="74a1f-117">Remarks</span></span>  
 <span data-ttu-id="74a1f-118">未解決のメソッドは宣言されましたが実装されていません。</span><span class="sxs-lookup"><span data-stu-id="74a1f-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="74a1f-119">メソッドがマークされている場合に、列挙体のメソッドが含まれている`miForwardRef`、`mdPinvokeImpl`または`miRuntime`は 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="74a1f-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="74a1f-120">つまり、未解決のメソッドは、マークされているクラス メソッド`miForwardRef`されませんが (PInvoke 経由で到達)、アンマネージ コードで実装やランタイム自体によって内部的に実装することは</span><span class="sxs-lookup"><span data-stu-id="74a1f-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="74a1f-121">列挙体は、モジュール スコープ (グローバル) で、またはインターフェイスまたは抽象クラスで定義されているすべてのメソッドを除外します。</span><span class="sxs-lookup"><span data-stu-id="74a1f-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74a1f-122">要件</span><span class="sxs-lookup"><span data-stu-id="74a1f-122">Requirements</span></span>  
 <span data-ttu-id="74a1f-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="74a1f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74a1f-124">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="74a1f-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="74a1f-125">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="74a1f-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="74a1f-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74a1f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a1f-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="74a1f-127">See Also</span></span>  
 [<span data-ttu-id="74a1f-128">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74a1f-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="74a1f-129">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74a1f-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
