---
title: "IMetaDataImport2 インターフェイス"
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
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7cd9d2cd2837ff43fbb266717546db3aa98190e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="0186b-102">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0186b-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="0186b-103">拡張、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)ジェネリック型の使用の機能を提供するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="0186b-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0186b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="0186b-104">Methods</span></span>  
  
|<span data-ttu-id="0186b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0186b-105">Method</span></span>|<span data-ttu-id="0186b-106">説明</span><span class="sxs-lookup"><span data-stu-id="0186b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0186b-107">EnumGenericParamConstraints メソッド</span><span class="sxs-lookup"><span data-stu-id="0186b-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="0186b-108">指定したトークンによって表されるジェネリック パラメーターに関連付けられているジェネリック パラメーターの制約の配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="0186b-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="0186b-109">EnumGenericParams メソッド</span><span class="sxs-lookup"><span data-stu-id="0186b-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="0186b-110">トークンのジェネリック パラメーターのトークンが、指定した TypeDef または MethodDef に関連付けられている配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="0186b-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="0186b-111">EnumMethodSpecs メソッド</span><span class="sxs-lookup"><span data-stu-id="0186b-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="0186b-112">トークンの MethodSpec トークンが指定した MethodDef または MemberRef に関連付けられている配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="0186b-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="0186b-113">GetGenericParamConstraintProps メソッド</span><span class="sxs-lookup"><span data-stu-id="0186b-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="0186b-114">指定された制約トークンによって表されるジェネリック パラメーターの制約に関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="0186b-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="0186b-115">GetGenericParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="0186b-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="0186b-116">指定したトークンによって表されるジェネリック パラメーターに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="0186b-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="0186b-117">GetMethodSpecProps メソッド</span><span class="sxs-lookup"><span data-stu-id="0186b-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="0186b-118">指定した MethodSpec によって参照されるメソッドのメタデータ署名のトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="0186b-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="0186b-119">GetPEKind メソッド</span><span class="sxs-lookup"><span data-stu-id="0186b-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="0186b-120">ポータブル実行可能 (PE) 内のコードの種類を識別する値ファイルを取得、通常、DLL または EXE ファイルで現在のメタデータ スコープで定義されています。</span><span class="sxs-lookup"><span data-stu-id="0186b-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="0186b-121">GetVersionString メソッド</span><span class="sxs-lookup"><span data-stu-id="0186b-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="0186b-122">アセンブリをビルドするために使用されたランタイムのバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="0186b-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0186b-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="0186b-123">Requirements</span></span>  
 <span data-ttu-id="0186b-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0186b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0186b-125">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0186b-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0186b-126">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="0186b-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0186b-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0186b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0186b-128">参照</span><span class="sxs-lookup"><span data-stu-id="0186b-128">See Also</span></span>  
 <xref:System.Reflection.PortableExecutableKinds>  
 [<span data-ttu-id="0186b-129">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0186b-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="0186b-130">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0186b-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
