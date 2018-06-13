---
title: IIdentityAuthority インターフェイス
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 692ac4ef4fe8ea64c6a63dc2f02cc04244a842c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432530"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="04b53-102">IIdentityAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="04b53-102">IIdentityAuthority Interface</span></span>
<span data-ttu-id="04b53-103">コード オブジェクトの id キーを管理します。</span><span class="sxs-lookup"><span data-stu-id="04b53-103">Manages identity keys for code objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="04b53-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="04b53-104">Methods</span></span>  
  
|<span data-ttu-id="04b53-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="04b53-105">Method</span></span>|<span data-ttu-id="04b53-106">説明</span><span class="sxs-lookup"><span data-stu-id="04b53-106">Description</span></span>|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="04b53-107">2 つ指定されているかどうかを示す値を取得[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)インスタンスが等しい。</span><span class="sxs-lookup"><span data-stu-id="04b53-107">Gets a value that indicates whether the two specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="04b53-108">2 つ指定されているかどうかを示す値を取得[IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)インスタンスが等しい。</span><span class="sxs-lookup"><span data-stu-id="04b53-108">Gets a value that indicates whether the two specified [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instances are equal.</span></span>|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="04b53-109">2 つの指定した文字列の定義 id の形式が等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="04b53-109">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|  
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="04b53-110">2 つの指定した文字列の参照 id の形式が等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="04b53-110">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|  
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="04b53-111">新しいへのポインターを取得`IDefinitionIdentity`を現在のスコープ内のコード オブジェクトを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="04b53-111">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="04b53-112">新しいへのポインターを取得`IReferenceIdentity`を現在のスコープ内のコード オブジェクトを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="04b53-112">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|  
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="04b53-113">指定した書式設定された文字列バージョンを取得`IDefinitionIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="04b53-113">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="04b53-114">指定した文字列形式を指定したワイド文字バッファーに設定`IDefinitionIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="04b53-114">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="04b53-115">示す値を取得するかどうか、指定した`IDefinitionIdentity`と`IReferenceIdentity`インスタンスが同じコード オブジェクトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="04b53-115">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="04b53-116">指定した文字列が同じコード オブジェクトを参照するかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="04b53-116">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|  
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="04b53-117">指定された文字列を新しく作成されたキーへのポインターを取得`IDefinitionIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="04b53-117">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="04b53-118">指定された文字列を新しく作成されたキーへのポインターを取得`IReferenceIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="04b53-118">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="04b53-119">指定したハッシュ値を取得`IDefinitionIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="04b53-119">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|  
|`IIdentityAuthority::HashReference`|<span data-ttu-id="04b53-120">指定したハッシュ値を取得`IreferenceIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="04b53-120">Gets a hash value for the specified `IreferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="04b53-121">指定した書式設定された文字列バージョンを取得`IReferenceIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="04b53-121">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="04b53-122">指定した文字列形式を指定したワイド文字バッファーに設定`IReferenceIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="04b53-122">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|  
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="04b53-123">インターフェイス ポインターを取得、`IDefinitionIdentity`形式の文字列の指定された対象から生成されたインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="04b53-123">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|  
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="04b53-124">インターフェイス ポインターを取得、`IReferenceIdentity`形式の文字列の指定された対象から生成されたインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="04b53-124">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04b53-125">要件</span><span class="sxs-lookup"><span data-stu-id="04b53-125">Requirements</span></span>  
 <span data-ttu-id="04b53-126">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="04b53-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04b53-127">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="04b53-127">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="04b53-128">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04b53-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b53-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="04b53-129">See Also</span></span>  
 [<span data-ttu-id="04b53-130">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="04b53-130">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
