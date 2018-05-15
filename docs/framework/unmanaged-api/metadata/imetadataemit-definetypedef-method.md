---
title: IMetaDataEmit::DefineTypeDef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54691785e3b2619b5f4a2eecc510800b4b5cee07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="0d551-102">IMetaDataEmit::DefineTypeDef メソッド</span><span class="sxs-lookup"><span data-stu-id="0d551-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="0d551-103">共通言語ランタイムの型の型定義を作成し、その種類の定義のメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="0d551-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d551-104">構文</span><span class="sxs-lookup"><span data-stu-id="0d551-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d551-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0d551-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="0d551-106">[in]Unicode での型の名前です。</span><span class="sxs-lookup"><span data-stu-id="0d551-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="0d551-107">[in]`TypeDef`属性。</span><span class="sxs-lookup"><span data-stu-id="0d551-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="0d551-108">これは、ビットマスク`CoreTypeAttr`値。</span><span class="sxs-lookup"><span data-stu-id="0d551-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="0d551-109">[in]基本クラスのトークンです。</span><span class="sxs-lookup"><span data-stu-id="0d551-109">[in] The token of the base class.</span></span> <span data-ttu-id="0d551-110">いずれかにする必要があります、`mdTypeDef`または`mdTypeRef`トークンです。</span><span class="sxs-lookup"><span data-stu-id="0d551-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="0d551-111">[in]このクラスまたはインターフェイスを実装するインターフェイスを指定するトークンの配列。</span><span class="sxs-lookup"><span data-stu-id="0d551-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="0d551-112">[out]`mdTypeDef`トークンが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="0d551-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d551-113">コメント</span><span class="sxs-lookup"><span data-stu-id="0d551-113">Remarks</span></span>  
 <span data-ttu-id="0d551-114">あるフラグ`dwTypeDefFlags`作成される型が共通型システムの参照型 (クラスまたはインターフェイス) または共通型システム値型かどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="0d551-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="0d551-115">指定されたパラメーターに応じて、このメソッド、副作用として作成することも、`mdInterfaceImpl`継承またはこの型によって実装されるインターフェイスごとに記録します。</span><span class="sxs-lookup"><span data-stu-id="0d551-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="0d551-116">ただし、このメソッドは返しませんこれら`mdInterfaceImpl`トークンです。</span><span class="sxs-lookup"><span data-stu-id="0d551-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="0d551-117">クライアントが後で追加または変更する場合、`mdInterfaceImpl`トークン、その必要がありますを使用して、`IMetaDataImport`それらを列挙するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="0d551-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="0d551-118">COM のセマンティクスを使用する場合、`[default]`インターフェイス内の最初の要素として既定のインターフェイスを指定する必要があります`rtkImplements`; カスタム属性をクラスに設定があることを示すクラスは既定のインターフェイス (が常に想定する、まず`mdInterfaceImpl`トークンで宣言されたクラス)。</span><span class="sxs-lookup"><span data-stu-id="0d551-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="0d551-119">各要素、`rtkImplements`配列を保持する`mdTypeDef`または`mdTypeRef`トークンです。</span><span class="sxs-lookup"><span data-stu-id="0d551-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="0d551-120">配列内の最後の要素である必要があります`mdTokenNil`です。</span><span class="sxs-lookup"><span data-stu-id="0d551-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d551-121">要件</span><span class="sxs-lookup"><span data-stu-id="0d551-121">Requirements</span></span>  
 <span data-ttu-id="0d551-122">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0d551-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d551-123">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0d551-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d551-124">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="0d551-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d551-125">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d551-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d551-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d551-126">See Also</span></span>  
 [<span data-ttu-id="0d551-127">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d551-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="0d551-128">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d551-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
