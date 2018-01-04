---
title: "IMetaDataImport::ResolveTypeRef メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.ResolveTypeRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64a783297b27c9d1400670eecb7dfe4cb69c2b96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="1050c-102">IMetaDataImport::ResolveTypeRef メソッド</span><span class="sxs-lookup"><span data-stu-id="1050c-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="1050c-103">解決、<xref:System.Type>参照を指定した TypeRef トークンによって表されます。</span><span class="sxs-lookup"><span data-stu-id="1050c-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1050c-104">構文</span><span class="sxs-lookup"><span data-stu-id="1050c-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1050c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1050c-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="1050c-106">[in]参照先の型情報を返す TypeRef メタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="1050c-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="1050c-107">[in]返されるインターフェイスの IID`ppIScope`です。</span><span class="sxs-lookup"><span data-stu-id="1050c-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="1050c-108">通常、IID_IMetaDataImport になります。</span><span class="sxs-lookup"><span data-stu-id="1050c-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="1050c-109">[out]参照先の型が定義されているモジュール スコープへのインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="1050c-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="1050c-110">[out]参照先の型を表す TypeDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1050c-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1050c-111">コメント</span><span class="sxs-lookup"><span data-stu-id="1050c-111">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1050c-112">複数のアプリケーション ドメインが読み込まれている場合は、このメソッドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1050c-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="1050c-113">メソッドは、アプリケーション ドメインの境界を考慮していません。</span><span class="sxs-lookup"><span data-stu-id="1050c-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="1050c-114">アセンブリの複数のバージョンが読み込まれ、同じ名前空間を持つ同じ型が含まれている場合は、このメソッドは、見つかった最初の種類のモジュールのスコープを返します。</span><span class="sxs-lookup"><span data-stu-id="1050c-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="1050c-115">`ResolveTypeRef`他のモジュールの種類の定義のメソッドを検索します。</span><span class="sxs-lookup"><span data-stu-id="1050c-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="1050c-116">見つかった場合は、型定義は、`ResolveTypeRef`そのモジュール スコープとした TypeDef トークンの種類のインターフェイスを返します。</span><span class="sxs-lookup"><span data-stu-id="1050c-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="1050c-117">型参照を解決するが AssemblyRef の解決スコープを持つ場合、`ResolveTypeRef`メソッドの呼び出しをいずれかに既に開かれたメタデータ スコープ内でだけの一致を検索、 [imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)メソッドまたは[imetadatadispenser::openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1050c-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="1050c-118">これは、ため`ResolveTypeRef`AssemblyRef スコープのみがディスク上またはグローバル アセンブリ キャッシュにアセンブリの格納場所を判別することはできません。</span><span class="sxs-lookup"><span data-stu-id="1050c-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1050c-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="1050c-119">Requirements</span></span>  
 <span data-ttu-id="1050c-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1050c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1050c-121">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1050c-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1050c-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1050c-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1050c-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1050c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1050c-124">参照</span><span class="sxs-lookup"><span data-stu-id="1050c-124">See Also</span></span>  
 [<span data-ttu-id="1050c-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1050c-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1050c-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1050c-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
