---
title: "IMetaDataEmit2 インターフェイス"
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
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 94180a1f844ac43d8a42be59ac4fca807a70ec70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2-interface"></a><span data-ttu-id="99827-102">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99827-102">IMetaDataEmit2 Interface</span></span>
<span data-ttu-id="99827-103">拡張、 [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)主に、ジェネリック型を処理する機能を提供するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="99827-103">Extends the [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface primarily to provide the ability to work with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99827-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="99827-104">Methods</span></span>  
  
|<span data-ttu-id="99827-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="99827-105">Method</span></span>|<span data-ttu-id="99827-106">説明</span><span class="sxs-lookup"><span data-stu-id="99827-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99827-107">DefineGenericParam メソッド</span><span class="sxs-lookup"><span data-stu-id="99827-107">DefineGenericParam Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|<span data-ttu-id="99827-108">ジェネリック型パラメーターの定義を作成し、そのジェネリック型パラメーターにトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="99827-108">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>|  
|[<span data-ttu-id="99827-109">DefineMethodSpec メソッド</span><span class="sxs-lookup"><span data-stu-id="99827-109">DefineMethodSpec Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|<span data-ttu-id="99827-110">メソッドのジェネリックのインスタンスを作成し、定義にトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="99827-110">Creates a generic instance of a method, and gets a token to the definition.</span></span>|  
|[<span data-ttu-id="99827-111">GetDeltaSaveSize メソッド</span><span class="sxs-lookup"><span data-stu-id="99827-111">GetDeltaSaveSize Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|<span data-ttu-id="99827-112">エディット コンティニュの現在のセッションに対する変更を表すために必要なデータのサイズの差を示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="99827-112">Gets a value indicating the difference in size of the data that is required to express the changes for the current edit-and-continue session.</span></span>|  
|[<span data-ttu-id="99827-113">ResetENCLog メソッド</span><span class="sxs-lookup"><span data-stu-id="99827-113">ResetENCLog Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|<span data-ttu-id="99827-114">エディット コンティニュは、ログをリセットし、新しいセッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="99827-114">Resets the edit-and-continue log and starts a new session.</span></span>|  
|[<span data-ttu-id="99827-115">SaveDelta メソッド</span><span class="sxs-lookup"><span data-stu-id="99827-115">SaveDelta Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|<span data-ttu-id="99827-116">エディット コンティニュの現在のセッションからの変更を指定したファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="99827-116">Saves changes from the current edit-and-continue session to the specified file.</span></span>|  
|[<span data-ttu-id="99827-117">SaveDeltaToMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="99827-117">SaveDeltaToMemory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|<span data-ttu-id="99827-118">エディット コンティニュの現在のセッションからの変更をメモリに保存します。</span><span class="sxs-lookup"><span data-stu-id="99827-118">Saves changes from the current edit-and-continue session to memory.</span></span>|  
|[<span data-ttu-id="99827-119">SaveDeltaToStream メソッド</span><span class="sxs-lookup"><span data-stu-id="99827-119">SaveDeltaToStream Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|<span data-ttu-id="99827-120">エディット コンティニュの現在のセッションからの変更を指定したストリームに保存します。</span><span class="sxs-lookup"><span data-stu-id="99827-120">Saves changes from the current edit-and-continue session to the specified stream.</span></span>|  
|[<span data-ttu-id="99827-121">SetGenericParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="99827-121">SetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|<span data-ttu-id="99827-122">指定したトークンによって参照されるジェネリック パラメーターの定義のプロパティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="99827-122">Sets property values for the generic parameter definition referenced by the specified token.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99827-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="99827-123">Requirements</span></span>  
 <span data-ttu-id="99827-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="99827-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99827-125">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="99827-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99827-126">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="99827-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="99827-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99827-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99827-128">参照</span><span class="sxs-lookup"><span data-stu-id="99827-128">See Also</span></span>  
 [<span data-ttu-id="99827-129">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99827-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="99827-130">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99827-130">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
