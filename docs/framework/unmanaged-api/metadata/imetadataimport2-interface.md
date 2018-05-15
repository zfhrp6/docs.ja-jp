---
title: IMetaDataImport2 インターフェイス
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1328e40c74c17c55cc476bba761c1c3be9af034e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="05ed2-102">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05ed2-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="05ed2-103">拡張、 [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)ジェネリック型の使用の機能を提供するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="05ed2-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05ed2-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="05ed2-104">Methods</span></span>  
  
|<span data-ttu-id="05ed2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="05ed2-105">Method</span></span>|<span data-ttu-id="05ed2-106">説明</span><span class="sxs-lookup"><span data-stu-id="05ed2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05ed2-107">EnumGenericParamConstraints メソッド</span><span class="sxs-lookup"><span data-stu-id="05ed2-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="05ed2-108">指定したトークンによって表されるジェネリック パラメーターに関連付けられているジェネリック パラメーターの制約の配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="05ed2-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="05ed2-109">EnumGenericParams メソッド</span><span class="sxs-lookup"><span data-stu-id="05ed2-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="05ed2-110">トークンのジェネリック パラメーターのトークンが、指定した TypeDef または MethodDef に関連付けられている配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="05ed2-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="05ed2-111">EnumMethodSpecs メソッド</span><span class="sxs-lookup"><span data-stu-id="05ed2-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="05ed2-112">トークンの MethodSpec トークンが指定した MethodDef または MemberRef に関連付けられている配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="05ed2-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="05ed2-113">GetGenericParamConstraintProps メソッド</span><span class="sxs-lookup"><span data-stu-id="05ed2-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="05ed2-114">指定された制約トークンによって表されるジェネリック パラメーターの制約に関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="05ed2-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="05ed2-115">GetGenericParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="05ed2-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="05ed2-116">指定したトークンによって表されるジェネリック パラメーターに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="05ed2-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="05ed2-117">GetMethodSpecProps メソッド</span><span class="sxs-lookup"><span data-stu-id="05ed2-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="05ed2-118">指定した MethodSpec によって参照されるメソッドのメタデータ署名のトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="05ed2-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="05ed2-119">GetPEKind メソッド</span><span class="sxs-lookup"><span data-stu-id="05ed2-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="05ed2-120">ポータブル実行可能 (PE) 内のコードの種類を識別する値ファイルを取得、通常、DLL または EXE ファイルで現在のメタデータ スコープで定義されています。</span><span class="sxs-lookup"><span data-stu-id="05ed2-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="05ed2-121">GetVersionString メソッド</span><span class="sxs-lookup"><span data-stu-id="05ed2-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="05ed2-122">アセンブリをビルドするために使用されたランタイムのバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="05ed2-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05ed2-123">要件</span><span class="sxs-lookup"><span data-stu-id="05ed2-123">Requirements</span></span>  
 <span data-ttu-id="05ed2-124">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="05ed2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05ed2-125">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="05ed2-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05ed2-126">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="05ed2-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05ed2-127">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05ed2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ed2-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="05ed2-128">See Also</span></span>  
 <xref:System.Reflection.PortableExecutableKinds>  
 [<span data-ttu-id="05ed2-129">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05ed2-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="05ed2-130">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05ed2-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
