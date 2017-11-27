---
title: "暗号設定スキーマ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c7d1e193236528c96e8253668c742883090ae188
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="b6a8a-102">暗号設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="b6a8a-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="b6a8a-103">暗号設定スキーマには、アルゴリズムの表示名を、暗号化アルゴリズムを実装するクラスに割り当てる方法を指定する要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b6a8a-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="b6a8a-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="b6a8a-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="b6a8a-105">**\<mscorlib>**</span><span class="sxs-lookup"><span data-stu-id="b6a8a-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="b6a8a-106">**\<cryptographySettings>**</span><span class="sxs-lookup"><span data-stu-id="b6a8a-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="b6a8a-107">**\<cryptoNameMapping>**</span><span class="sxs-lookup"><span data-stu-id="b6a8a-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="b6a8a-108">**\<cryptoClasses>**</span><span class="sxs-lookup"><span data-stu-id="b6a8a-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="b6a8a-109">**\<cryptoClass>**</span><span class="sxs-lookup"><span data-stu-id="b6a8a-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="b6a8a-110">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="b6a8a-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="b6a8a-111">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="b6a8a-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="b6a8a-112">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="b6a8a-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="b6a8a-113">要素</span><span class="sxs-lookup"><span data-stu-id="b6a8a-113">Element</span></span>|<span data-ttu-id="b6a8a-114">説明</span><span class="sxs-lookup"><span data-stu-id="b6a8a-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6a8a-115">**\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="b6a8a-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="b6a8a-116">**\<nameEntry>** 要素内の表示名へのマッピングを持つ暗号化クラスのリストを含みます。</span><span class="sxs-lookup"><span data-stu-id="b6a8a-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="b6a8a-117">**\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="b6a8a-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="b6a8a-118">**\<nameEntry>** 要素内の表示名へのマッピングを持つ暗号化クラスを含みます。</span><span class="sxs-lookup"><span data-stu-id="b6a8a-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="b6a8a-119">**\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="b6a8a-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="b6a8a-120">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="b6a8a-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="b6a8a-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="b6a8a-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="b6a8a-122">表示名へのクラスのマッピングを含みます。</span><span class="sxs-lookup"><span data-stu-id="b6a8a-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="b6a8a-123">**\<mscorlib>** 要素、暗号化設定用</span><span class="sxs-lookup"><span data-stu-id="b6a8a-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="b6a8a-124">**\<cryptographySettings >**要素を含みます。</span><span class="sxs-lookup"><span data-stu-id="b6a8a-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="b6a8a-125">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="b6a8a-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="b6a8a-126">アルゴリズムの表示名にクラス名をマップして、1 つのクラスが多くの表示名を持つことを許可します。</span><span class="sxs-lookup"><span data-stu-id="b6a8a-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="b6a8a-127">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="b6a8a-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="b6a8a-128">ASN.1 オブジェクト識別子 (OID) を表示名にマップします。</span><span class="sxs-lookup"><span data-stu-id="b6a8a-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="b6a8a-129">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="b6a8a-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="b6a8a-130">クラスへの ASN.1 OID マッピングを含みます。</span><span class="sxs-lookup"><span data-stu-id="b6a8a-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6a8a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6a8a-131">See Also</span></span>  
 [<span data-ttu-id="b6a8a-132">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="b6a8a-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="b6a8a-133">暗号サービス</span><span class="sxs-lookup"><span data-stu-id="b6a8a-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
