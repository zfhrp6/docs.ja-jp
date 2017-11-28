---
title: "IMetaDataEmit::SetClassLayout メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a68d94cbea408bee90b117965f83f760ba7ea5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="19065-102">IMetaDataEmit::SetClassLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="19065-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="19065-103">前回の呼び出しで定義されているクラスのフィールドのレイアウトが完了した[DefineTypeDef メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="19065-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19065-104">構文</span><span class="sxs-lookup"><span data-stu-id="19065-104">Syntax</span></span>  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19065-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="19065-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="19065-106">[in]`mdTypeDef`レイアウトされるクラスを指定するトークン。</span><span class="sxs-lookup"><span data-stu-id="19065-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="19065-107">[in]パッキング サイズ: 1、2、4、8 バイトまたは 16 バイトです。</span><span class="sxs-lookup"><span data-stu-id="19065-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="19065-108">パッキング サイズは、横にあるフィールド間のバイト数です。</span><span class="sxs-lookup"><span data-stu-id="19065-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="19065-109">[in]配列[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)構造体、クラスのフィールドとフィールドのクラス内でオフセットをそれぞれ指定します。</span><span class="sxs-lookup"><span data-stu-id="19065-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="19065-110">配列を終了`mdTokenNil`です。</span><span class="sxs-lookup"><span data-stu-id="19065-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="19065-111">[in]クラスのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="19065-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19065-112">コメント</span><span class="sxs-lookup"><span data-stu-id="19065-112">Remarks</span></span>  
 <span data-ttu-id="19065-113">クラスが最初に呼び出すことによって定義されている、 [imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)メソッド、およびクラスのフィールドについて次の 3 つのレイアウトのいずれかを指定する: 自動、シーケンシャル、または明示的なです。</span><span class="sxs-lookup"><span data-stu-id="19065-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="19065-114">通常は自動レイアウトを使用してランタイムにフィールドをレイアウトする最善の方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="19065-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="19065-115">ただし、フィールドをアンマネージ コードが使用する配置に従ってレイアウトが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="19065-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="19065-116">この例では、シーケンシャルまたは明示的なレイアウトと呼び出しを選択して`SetClassLayout`フィールドのレイアウトを完了します。</span><span class="sxs-lookup"><span data-stu-id="19065-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
-   <span data-ttu-id="19065-117">シーケンシャル レイアウト: パッキング サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="19065-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="19065-118">フィールドは、自然なサイズ、またはどの結果フィールドのオフセットは小さく、パッキング サイズに従って配置します。</span><span class="sxs-lookup"><span data-stu-id="19065-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="19065-119">設定`rFieldOffsets`と`ulClassSize`をゼロにします。</span><span class="sxs-lookup"><span data-stu-id="19065-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
-   <span data-ttu-id="19065-120">明示的なレイアウト: 各フィールドのオフセットを指定するか、クラスのサイズおよびパッキング サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="19065-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19065-121">要件</span><span class="sxs-lookup"><span data-stu-id="19065-121">Requirements</span></span>  
 <span data-ttu-id="19065-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="19065-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19065-123">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="19065-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19065-124">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="19065-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19065-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19065-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19065-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="19065-126">See Also</span></span>  
 [<span data-ttu-id="19065-127">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="19065-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="19065-128">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="19065-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
