---
title: "IMetaDataDispenserEx インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx
helpviewer_keywords: IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4cf062029647d4834118a459db378c8535182daf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="f5bbb-102">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5bbb-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="f5bbb-103">拡張、 [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)メタデータ Api が現在のメタデータ スコープにどのように動作する方法を制御する機能を提供するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5bbb-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="f5bbb-104">Methods</span></span>  
  
|<span data-ttu-id="f5bbb-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="f5bbb-105">Method</span></span>|<span data-ttu-id="f5bbb-106">説明</span><span class="sxs-lookup"><span data-stu-id="f5bbb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5bbb-107">FindAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="f5bbb-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="f5bbb-108">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-108">This method is not implemented.</span></span> <span data-ttu-id="f5bbb-109">呼び出された場合、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="f5bbb-110">FindAssemblyModule メソッド</span><span class="sxs-lookup"><span data-stu-id="f5bbb-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="f5bbb-111">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-111">This method is not implemented.</span></span> <span data-ttu-id="f5bbb-112">呼び出された場合、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="f5bbb-113">GetCORSystemDirectory メソッド</span><span class="sxs-lookup"><span data-stu-id="f5bbb-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="f5bbb-114">現在の共通言語ランタイム (CLR) を保持するディレクトリを取得します。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="f5bbb-115">このメソッドは、アウト プロセスのデバッガーで使用するためだけサポートします。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="f5bbb-116">別のコンポーネントから呼び出す場合、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="f5bbb-117">GetOption メソッド</span><span class="sxs-lookup"><span data-stu-id="f5bbb-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="f5bbb-118">現在のメタデータ スコープに指定されたオプションの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="f5bbb-119">オプションは、現在のメタデータ スコープへの呼び出しの処理方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="f5bbb-120">OpenScopeOnITypeInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="f5bbb-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="f5bbb-121">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-121">This method is not implemented.</span></span> <span data-ttu-id="f5bbb-122">呼び出された場合、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="f5bbb-123">SetOption メソッド</span><span class="sxs-lookup"><span data-stu-id="f5bbb-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="f5bbb-124">現在のメタデータ スコープに指定された値を指定されたオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="f5bbb-125">オプションは、現在のメタデータ スコープへの呼び出しの処理方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5bbb-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="f5bbb-126">Requirements</span></span>  
 <span data-ttu-id="f5bbb-127">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f5bbb-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5bbb-128">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f5bbb-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f5bbb-129">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="f5bbb-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f5bbb-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5bbb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5bbb-131">参照</span><span class="sxs-lookup"><span data-stu-id="f5bbb-131">See Also</span></span>  
 [<span data-ttu-id="f5bbb-132">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5bbb-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="f5bbb-133">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5bbb-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="f5bbb-134">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5bbb-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f5bbb-135">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5bbb-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
