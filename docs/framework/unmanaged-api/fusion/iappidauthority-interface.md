---
title: "IAppIdAuthority インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppIdAuthority
api_location: fusion.dll
api_type: COM
f1_keywords: IAppIdAuthority
helpviewer_keywords: IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07bfd26a43d264babc9854b0fd0da909dd329405
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="3a98a-102">IAppIdAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a98a-102">IAppIdAuthority Interface</span></span>
<span data-ttu-id="3a98a-103">メソッドを生成し、アプリケーションの id と参照キーの比較を提供します。</span><span class="sxs-lookup"><span data-stu-id="3a98a-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a98a-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="3a98a-104">Methods</span></span>  
  
|<span data-ttu-id="3a98a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3a98a-105">Method</span></span>|<span data-ttu-id="3a98a-106">説明</span><span class="sxs-lookup"><span data-stu-id="3a98a-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="3a98a-107">2 つ指定されているかどうかを示す値を取得[IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)インスタンスが等しい。</span><span class="sxs-lookup"><span data-stu-id="3a98a-107">Gets a value that indicates whether the two specified [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="3a98a-108">フラグの値をそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="3a98a-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="3a98a-109">2 つ指定されているかどうかを示す値を取得[IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)インスタンスが等しい。</span><span class="sxs-lookup"><span data-stu-id="3a98a-109">Gets a value that indicates whether the two specified [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="3a98a-110">フラグの値をそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="3a98a-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="3a98a-111">2 つの指定した文字列の定義が等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="3a98a-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="3a98a-112">フラグの値をそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="3a98a-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="3a98a-113">2 つの指定した文字列参照が等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="3a98a-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="3a98a-114">フラグの値をそれぞれのバージョン情報を無視する IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="3a98a-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="3a98a-115">新しく生成されたインターフェイス ポインターを取得`IDefinitionAppId`を現在のスコープ内のアセンブリを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="3a98a-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="3a98a-116">新しく作成するインターフェイス ポインターを取得`IReferenceAppId`を表す現在のスコープ内のアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="3a98a-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="3a98a-117">指定した文字列形式を取得`IDefinitionAppId`、指定したフラグの値を使用します。</span><span class="sxs-lookup"><span data-stu-id="3a98a-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="3a98a-118">示す値を取得するかどうか、指定した`IDefinitionAppId`と`IReferenceAppId`同じアセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="3a98a-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="3a98a-119">指定した定義の文字列と参照文字列が同じアセンブリを表すかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="3a98a-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="3a98a-120">表す、指定した文字列のキーを取得`IDefinitionAppId`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="3a98a-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="3a98a-121">表す、指定した文字列のキーを取得`IReferenceAppId`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="3a98a-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="3a98a-122">指定したハッシュ キーを取得`IDefinitionAppId`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="3a98a-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="3a98a-123">指定したハッシュ キーを取得`IReferenceAppId`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="3a98a-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="3a98a-124">指定した文字列形式を取得`IReferenceAppId`、指定したフラグの値を使用します。</span><span class="sxs-lookup"><span data-stu-id="3a98a-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="3a98a-125">インターフェイス ポインターを取得、`IDefinitionAppId`を指定した文字列キーによって参照されるアセンブリを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="3a98a-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="3a98a-126">インターフェイス ポインターを取得、`IReferenceAppId`を指定した文字列キーによって参照されるアセンブリを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="3a98a-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a98a-127">要件</span><span class="sxs-lookup"><span data-stu-id="3a98a-127">Requirements</span></span>  
 <span data-ttu-id="3a98a-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3a98a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a98a-129">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="3a98a-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="3a98a-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a98a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a98a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a98a-131">See Also</span></span>  
 [<span data-ttu-id="3a98a-132">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a98a-132">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
