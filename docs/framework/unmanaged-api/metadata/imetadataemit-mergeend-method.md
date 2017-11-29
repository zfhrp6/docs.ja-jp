---
title: "IMetaDataEmit::MergeEnd メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.MergeEnd
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 57fbecd05f0eaee48e9dc8a599e3174ac97033f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitmergeend-method"></a><span data-ttu-id="c7f66-102">IMetaDataEmit::MergeEnd メソッド</span><span class="sxs-lookup"><span data-stu-id="c7f66-102">IMetaDataEmit::MergeEnd Method</span></span>
<span data-ttu-id="c7f66-103">現在のマージのスコープを 1 つまたは複数の以前の呼び出しで指定されたすべてのメタデータ スコープ[imetadataemit::merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="c7f66-103">Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7f66-104">構文</span><span class="sxs-lookup"><span data-stu-id="c7f66-104">Syntax</span></span>  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7f66-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c7f66-105">Parameters</span></span>  
 <span data-ttu-id="c7f66-106">このメソッドには、パラメーターはありません。</span><span class="sxs-lookup"><span data-stu-id="c7f66-106">This method takes no parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7f66-107">コメント</span><span class="sxs-lookup"><span data-stu-id="c7f66-107">Remarks</span></span>  
 <span data-ttu-id="c7f66-108">このルーチンは、メタデータの実際のマージをトリガー、すべてのインポート前に呼び出しを追加して指定した範囲`IMetaDataEmit::Merge`、現在の出力のスコープにします。</span><span class="sxs-lookup"><span data-stu-id="c7f66-108">This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.</span></span>  
  
 <span data-ttu-id="c7f66-109">次の特殊な条件は、マージに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c7f66-109">The following special conditions apply to the merge:</span></span>  
  
-   <span data-ttu-id="c7f66-110">モジュールのバージョン id (MVID) インポートされることは、インポートのスコープ内のメタデータを一意になっているためです。</span><span class="sxs-lookup"><span data-stu-id="c7f66-110">A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.</span></span>  
  
-   <span data-ttu-id="c7f66-111">既存のモジュール全体のプロパティは上書きされません。</span><span class="sxs-lookup"><span data-stu-id="c7f66-111">No existing module-wide properties are overwritten.</span></span>  
  
     <span data-ttu-id="c7f66-112">モジュールのプロパティが既に設定されている現在のスコープのモジュールのプロパティはインポートされません。</span><span class="sxs-lookup"><span data-stu-id="c7f66-112">If module properties were already set for the current scope, no module properties are imported.</span></span> <span data-ttu-id="c7f66-113">ただし、現在のスコープでこのモジュールのプロパティが設定されていない場合、最初に検出された、1 回だけがインポートされます。</span><span class="sxs-lookup"><span data-stu-id="c7f66-113">However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered.</span></span> <span data-ttu-id="c7f66-114">これらのモジュールのプロパティが再度発生する場合、重複しています。</span><span class="sxs-lookup"><span data-stu-id="c7f66-114">If those module properties are encountered again, they are duplicates.</span></span> <span data-ttu-id="c7f66-115">(MVID) を除くすべてのモジュールのプロパティの値を比較し、重複部分が見つからない、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c7f66-115">If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.</span></span>  
  
-   <span data-ttu-id="c7f66-116">型の定義 (`TypeDef`)、現在のスコープに重複がマージされません。</span><span class="sxs-lookup"><span data-stu-id="c7f66-116">For type definitions (`TypeDef`), no duplicates are merged into the current scope.</span></span> <span data-ttu-id="c7f66-117">`TypeDef`オブジェクトはそれぞれに対して重複をチェック*オブジェクトの完全修飾名* + *GUID* + *バージョン番号*です。</span><span class="sxs-lookup"><span data-stu-id="c7f66-117">`TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*.</span></span> <span data-ttu-id="c7f66-118">名前または GUID のいずれかに一致があるその他の 2 つの要素のいずれかが異なる場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c7f66-118">If there is a match on either name or GUID, and any of the other two elements is different, an error is raised.</span></span> <span data-ttu-id="c7f66-119">それ以外の場合、3 つの項目をすべて一致する場合、`MergeEnd`エントリが重複しないことを確認するにはない場合、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c7f66-119">Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised.</span></span> <span data-ttu-id="c7f66-120">この簡単なチェックを探します。</span><span class="sxs-lookup"><span data-stu-id="c7f66-120">This cursory check looks for:</span></span>  
  
    -   <span data-ttu-id="c7f66-121">同じメンバー宣言と同じ順序で発生しています。</span><span class="sxs-lookup"><span data-stu-id="c7f66-121">The same member declarations, occurring in the same order.</span></span> <span data-ttu-id="c7f66-122">メンバーとしてフラグが付いている`mdPrivateScope`(を参照してください、 [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列挙型) です。 この確認に含まれていない特別にマージされます。</span><span class="sxs-lookup"><span data-stu-id="c7f66-122">Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.</span></span>  
  
    -   <span data-ttu-id="c7f66-123">同じクラス レイアウトです。</span><span class="sxs-lookup"><span data-stu-id="c7f66-123">The same class layout.</span></span>  
  
     <span data-ttu-id="c7f66-124">つまり、`TypeDef`オブジェクト必要があります常に完全かつ一貫して定義するすべてのメタデータ スコープ内で宣言されている以外の完全定義があると見なされます (クラス) のメンバーの実装が複数のコンパイル単位に分散している場合すべてのスコープ内に存在しスコープごとにインクリメントは行われません。</span><span class="sxs-lookup"><span data-stu-id="c7f66-124">This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope.</span></span> <span data-ttu-id="c7f66-125">たとえば、パラメーター名が、コントラクトに関連する場合は、する必要がありますに出力すると同じ方法すべてのスコープ関連する、ない場合、必要があるメタデータに対して出力されません。</span><span class="sxs-lookup"><span data-stu-id="c7f66-125">For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.</span></span>  
  
     <span data-ttu-id="c7f66-126">例外は、`TypeDef`オブジェクトとしてフラグが設定された増分のメンバーを持つことができます`mdPrivateScope`です。</span><span class="sxs-lookup"><span data-stu-id="c7f66-126">The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`.</span></span> <span data-ttu-id="c7f66-127">これらは、発生時に`MergeEnd`増分重複に関係なく、現在のスコープに追加します。</span><span class="sxs-lookup"><span data-stu-id="c7f66-127">On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates.</span></span> <span data-ttu-id="c7f66-128">コンパイラは、プライベートのスコープを認識するため、コンパイラが規則を適用する行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7f66-128">Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.</span></span>  
  
-   <span data-ttu-id="c7f66-129">相対仮想アドレス (Rva) のインポートまたは; トピックとマージされていません。コンパイラは、この情報を再生成すると想定されます。</span><span class="sxs-lookup"><span data-stu-id="c7f66-129">Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.</span></span>  
  
-   <span data-ttu-id="c7f66-130">アタッチされている項目がマージされた場合にのみ、カスタム属性がマージされます。</span><span class="sxs-lookup"><span data-stu-id="c7f66-130">Custom attributes are merged only when the item to which they are attached is merged.</span></span> <span data-ttu-id="c7f66-131">たとえば、クラスに関連付けられているカスタム属性は、クラスが最初に検出されたときにマージされます。</span><span class="sxs-lookup"><span data-stu-id="c7f66-131">For example, custom attributes associated with a class are merged when the class is first encountered.</span></span> <span data-ttu-id="c7f66-132">カスタム属性が関連付けられている場合、`TypeDef`または`MemberDef`(メンバー コンパイルのタイムスタンプ) などのコンパイル単位に固有であるはマージされませんおよび削除するか、このようなメタデータを更新するコンパイラの責任です。</span><span class="sxs-lookup"><span data-stu-id="c7f66-132">If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7f66-133">要件</span><span class="sxs-lookup"><span data-stu-id="c7f66-133">Requirements</span></span>  
 <span data-ttu-id="c7f66-134">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c7f66-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7f66-135">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c7f66-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7f66-136">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="c7f66-136">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7f66-137">**.NET framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7f66-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f66-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7f66-138">See Also</span></span>  
 [<span data-ttu-id="c7f66-139">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7f66-139">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="c7f66-140">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7f66-140">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
