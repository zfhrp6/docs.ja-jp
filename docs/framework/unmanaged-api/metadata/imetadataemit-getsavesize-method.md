---
title: "IMetaDataEmit::GetSaveSize メソッド"
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
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7585f6adbca97b252fdad90276b0cd422d32c04a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="47717-102">IMetaDataEmit::GetSaveSize メソッド</span><span class="sxs-lookup"><span data-stu-id="47717-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="47717-103">現在のスコープ内には、バイナリの推定サイズ アセンブリとそのメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="47717-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47717-104">構文</span><span class="sxs-lookup"><span data-stu-id="47717-104">Syntax</span></span>  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47717-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="47717-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="47717-106">[in]値、 [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md)正確またはおおよそのサイズを取得するかどうかを指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="47717-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="47717-107">有効な値は 3 つだけ: cssAccurate、cssQuick、および cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="47717-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
-   <span data-ttu-id="47717-108">cssAccurate では、正確な保存のサイズを返しますが、計算に時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="47717-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
-   <span data-ttu-id="47717-109">cssQuick は安全性、用に埋め込まれて、サイズを返しますが、計算時間がかかりません。</span><span class="sxs-lookup"><span data-stu-id="47717-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
-   <span data-ttu-id="47717-110">cssDiscardTransientCAs 指示`GetSaveSize`ことができますを破棄破棄できるカスタム属性です。</span><span class="sxs-lookup"><span data-stu-id="47717-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="47717-111">[out]ファイルを保存するために必要なサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="47717-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47717-112">コメント</span><span class="sxs-lookup"><span data-stu-id="47717-112">Remarks</span></span>  
 <span data-ttu-id="47717-113">`GetSaveSize`必要に応じて、(バイト単位) を現在のスコープ内のアセンブリとそのすべてのメタデータを保存する領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="47717-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="47717-114">(への呼び出し、 [imetadataemit::savetostream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md)メソッドはこのバイト数を出力します)。</span><span class="sxs-lookup"><span data-stu-id="47717-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="47717-115">呼び出し元が実装されている場合、 [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)インターフェイス (を通じて[imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)または[imetadataemit::merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md))、`GetSaveSize`は 2 つのパスを実行最適化し、それを圧縮するメタデータ。</span><span class="sxs-lookup"><span data-stu-id="47717-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="47717-116">それ以外の場合、最適化は行われません。</span><span class="sxs-lookup"><span data-stu-id="47717-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="47717-117">最適化を実行すると、最初のパスは単にインポート時の検索のパフォーマンスを調整するメタデータ構造体を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="47717-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="47717-118">この手順は、通常、レコードが移動、今後の参照用のツールで保持されるトークンが無効にした、副作用とで発生します。</span><span class="sxs-lookup"><span data-stu-id="47717-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="47717-119">メタデータに通知しませんまでこれらのトークンの変更の呼び出し元は、2 番目のパスの後にただしです。</span><span class="sxs-lookup"><span data-stu-id="47717-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="47717-120">2 番目のパスでは、さまざまな最適化が実行退席中の (事前バインディング) の最適化などのメタデータの全体的なサイズの削減を意図した`mdTypeRef`と`mdMemberRef`トークンの参照先が型またはメンバーで宣言されているときに、現在のメタデータ スコープ。</span><span class="sxs-lookup"><span data-stu-id="47717-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="47717-121">このパスでは、トークンのマッピングの別のラウンドが発生します。</span><span class="sxs-lookup"><span data-stu-id="47717-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="47717-122">このパスの後はメタデータ エンジンに通知、呼び出し元からその`IMapToken`のいずれかのインターフェイスは、トークンの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="47717-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47717-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="47717-123">Requirements</span></span>  
 <span data-ttu-id="47717-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="47717-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47717-125">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="47717-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="47717-126">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="47717-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47717-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47717-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47717-128">参照</span><span class="sxs-lookup"><span data-stu-id="47717-128">See Also</span></span>  
 [<span data-ttu-id="47717-129">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="47717-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="47717-130">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="47717-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
