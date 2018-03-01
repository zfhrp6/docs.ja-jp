---
title: "IMetaDataConverter インターフェイス"
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
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 758ea4261b859773c600ca91d52e3a9053776136
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="1a65b-102">IMetaDataConverter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1a65b-102">IMetaDataConverter Interface</span></span>
<span data-ttu-id="1a65b-103">タイプ ライブラリをそれぞれのメタデータ署名にマップして、一方から他方に変換するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="1a65b-103">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a65b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="1a65b-104">Methods</span></span>  
  
|<span data-ttu-id="1a65b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1a65b-105">Method</span></span>|<span data-ttu-id="1a65b-106">説明</span><span class="sxs-lookup"><span data-stu-id="1a65b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a65b-107">GetMetaDataFromTypeInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="1a65b-107">GetMetaDataFromTypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="1a65b-108">ポインターを取得、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)を指定したによって参照されるタイプ ライブラリのメタデータ シグネチャを表すインスタンス`ITypeInfo`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="1a65b-108">Gets a pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="1a65b-109">GetMetaDataFromTypeLib メソッド</span><span class="sxs-lookup"><span data-stu-id="1a65b-109">GetMetaDataFromTypeLib Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="1a65b-110">ポインターを取得、`IMetaDataImport`を指定したによって表されるタイプ ライブラリのメタデータ シグネチャを表すインスタンス`ITypeLib`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="1a65b-110">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="1a65b-111">GetTypeLibFromMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="1a65b-111">GetTypeLibFromMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="1a65b-112">ポインターを取得、`ITypeLib`を指定されたモジュールとライブラリの名前を持つタイプ ライブラリを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="1a65b-112">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a65b-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="1a65b-113">Requirements</span></span>  
 <span data-ttu-id="1a65b-114">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1a65b-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a65b-115">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1a65b-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a65b-116">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="1a65b-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a65b-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a65b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a65b-118">参照</span><span class="sxs-lookup"><span data-stu-id="1a65b-118">See Also</span></span>  
 [<span data-ttu-id="1a65b-119">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1a65b-119">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="1a65b-120">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1a65b-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
