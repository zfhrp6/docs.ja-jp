---
title: IMetaDataEmit::DefineImportMember メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f9995fda70d1d5a3c19c30496de6c32f20015d47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449391"
---
# <a name="imetadataemitdefineimportmember-method"></a><span data-ttu-id="4c565-102">IMetaDataEmit::DefineImportMember メソッド</span><span class="sxs-lookup"><span data-stu-id="4c565-102">IMetaDataEmit::DefineImportMember Method</span></span>
<span data-ttu-id="4c565-103">型または現在のスコープ外に定義され、その参照のトークンを定義するモジュールの指定されたメンバーへの参照を作成します。</span><span class="sxs-lookup"><span data-stu-id="4c565-103">Creates a reference to the specified member of a type or module that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c565-104">構文</span><span class="sxs-lookup"><span data-stu-id="4c565-104">Syntax</span></span>  
  
```  
HRESULT DefineImportMember (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,   
    [in]  mdToken                  mbMember,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [in]  mdToken                  tkParent,   
    [out] mdMemberRef              *pmr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c565-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4c565-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="4c565-106">[in][IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)対象メンバーのインポート元となるアセンブリを表すインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="4c565-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target member is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="4c565-107">[in]指定されたアセンブリのハッシュを含む配列`pAssemImport`です。</span><span class="sxs-lookup"><span data-stu-id="4c565-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="4c565-108">[in] `pbHashValue` 配列のバイト数。</span><span class="sxs-lookup"><span data-stu-id="4c565-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="4c565-109">[in][IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)対象メンバーのインポート元のメタデータ スコープを表すインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="4c565-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target member is imported.</span></span>  
  
 `mbMember`  
 <span data-ttu-id="4c565-110">[in]対象メンバーを指定するメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="4c565-110">[in] The metadata token that specifies the target member.</span></span> <span data-ttu-id="4c565-111">トークンを指定できます、 `mdMethodDef` (メンバー メソッドの)、 `mdProperty` (のメンバー プロパティの場合) または`mdFieldDef`(メンバー フィールド) のトークン。</span><span class="sxs-lookup"><span data-stu-id="4c565-111">The token can be an `mdMethodDef` (for a member method), `mdProperty` (for a member property), or `mdFieldDef` (for a member field) token.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="4c565-112">[in][IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)対象メンバーのインポート先のアセンブリを表すインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="4c565-112">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target member is imported.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="4c565-113">[in]`mdTypeRef`または`mdModuleRef`型またはモジュールのトークンを所有する対象のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="4c565-113">[in] The `mdTypeRef` or `mdModuleRef` token for the type or module, respectively, that owns the target member.</span></span>  
  
 `pmr`  
 <span data-ttu-id="4c565-114">[out]`mdMemberRef`メンバー参照の現在のスコープで定義されているトークンです。</span><span class="sxs-lookup"><span data-stu-id="4c565-114">[out] The `mdMemberRef` token that is defined in the current scope for the member reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c565-115">コメント</span><span class="sxs-lookup"><span data-stu-id="4c565-115">Remarks</span></span>  
 <span data-ttu-id="4c565-116">`DefineImportMember`メソッドは、によって指定されたメンバーを検索`mbMember`、つまりで指定された別のスコープで定義されている`pImport`、およびそのプロパティを取得します。</span><span class="sxs-lookup"><span data-stu-id="4c565-116">The `DefineImportMember` method looks up the member, specified by `mbMember`, that is defined in another scope, specified by `pImport`, and retrieves its properties.</span></span> <span data-ttu-id="4c565-117">呼び出しにこの情報を使用して、 [imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)メンバー参照を作成する、現在のスコープ内のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="4c565-117">It uses this information to call the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method in the current scope to create the member reference.</span></span>  
  
 <span data-ttu-id="4c565-118">使用する前に、一般に、`DefineImportMember`メソッドを作成する必要が、現在のスコープは、型参照またはターゲット メンバーの親クラス、インターフェイス、またはモジュールのモジュール参照します。</span><span class="sxs-lookup"><span data-stu-id="4c565-118">Generally, before you use the `DefineImportMember` method, you must create, in the current scope, a type reference or module reference for the target member's parent class, interface, or module.</span></span> <span data-ttu-id="4c565-119">この参照のメタデータ トークンが渡され、`tkParent`引数。</span><span class="sxs-lookup"><span data-stu-id="4c565-119">The metadata token for this reference is then passed in the `tkParent` argument.</span></span> <span data-ttu-id="4c565-120">コンパイラやリンカーによって後で解決する場合は、対象のメンバーの親への参照を作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4c565-120">You do not need to create a reference to the target member's parent if it will be resolved later by the compiler or linker.</span></span> <span data-ttu-id="4c565-121">まとめ</span><span class="sxs-lookup"><span data-stu-id="4c565-121">To summarize:</span></span>  
  
-   <span data-ttu-id="4c565-122">対象のメンバーがフィールドまたはメソッドの場合を使用するか、 [imetadataemit::definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)または[imetadataemit::defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)の現在のスコープ内の型参照を作成する方法、メンバーの親クラスまたはインターフェイスの親。</span><span class="sxs-lookup"><span data-stu-id="4c565-122">If the target member is a field or method, use either the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) or the [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
-   <span data-ttu-id="4c565-123">対象のメンバーが、グローバル変数またはグローバル関数 (つまりのメンバーでないクラスまたはインターフェイス) の場合を使用して、 [imetadataemit::definemoduleref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)メンバーの親の現在のスコープでモジュール参照を作成する方法モジュール。</span><span class="sxs-lookup"><span data-stu-id="4c565-123">If the target member is a global variable or global function (that is, not a member of a class or interface), use the [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) method to create a module reference, in the current scope, for the member's parent module.</span></span>  
  
-   <span data-ttu-id="4c565-124">対象メンバーの親は、コンパイラやリンカーによって後で解決は、その渡す`mdTokenNil`で`tkParent`です。</span><span class="sxs-lookup"><span data-stu-id="4c565-124">If the target member's parent will be resolved later by the compiler or linker, then pass `mdTokenNil` in `tkParent`.</span></span> <span data-ttu-id="4c565-125">これが適用される唯一のシナリオがグローバル関数またはグローバル変数が、現在のモジュールに最終的にリンクされる .obj ファイルからインポートされる、マージされたメタデータです。</span><span class="sxs-lookup"><span data-stu-id="4c565-125">The only scenario in which this applies is when a global function or global variable is being imported from a .obj file that will ultimately be linked into the current module and the metadata merged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c565-126">要件</span><span class="sxs-lookup"><span data-stu-id="4c565-126">Requirements</span></span>  
 <span data-ttu-id="4c565-127">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4c565-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c565-128">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4c565-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c565-129">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="4c565-129">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c565-130">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c565-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c565-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c565-131">See Also</span></span>  
 [<span data-ttu-id="4c565-132">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4c565-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4c565-133">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4c565-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
