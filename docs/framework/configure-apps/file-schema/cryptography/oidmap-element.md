---
title: "&lt;oidMap&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 08f7eb8e4531d27586bede11bacf598e472b158f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltoidmapgt-element"></a><span data-ttu-id="ecc33-102">&lt;oidMap&gt;要素</span><span class="sxs-lookup"><span data-stu-id="ecc33-102">&lt;oidMap&gt; Element</span></span>
<span data-ttu-id="ecc33-103">クラスに ASN.1 オブジェクト識別子 (OID) のマッピングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ecc33-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  
  
 <span data-ttu-id="ecc33-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ecc33-104">\<configuration></span></span>  
<span data-ttu-id="ecc33-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="ecc33-105">\<mscorlib></span></span>  
<span data-ttu-id="ecc33-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="ecc33-106">\<cryptographySettings></span></span>  
<span data-ttu-id="ecc33-107">\<oidMap ></span><span class="sxs-lookup"><span data-stu-id="ecc33-107">\<oidMap></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc33-108">構文</span><span class="sxs-lookup"><span data-stu-id="ecc33-108">Syntax</span></span>  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecc33-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ecc33-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ecc33-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ecc33-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecc33-111">属性</span><span class="sxs-lookup"><span data-stu-id="ecc33-111">Attributes</span></span>  
 <span data-ttu-id="ecc33-112">なし。</span><span class="sxs-lookup"><span data-stu-id="ecc33-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ecc33-113">子要素</span><span class="sxs-lookup"><span data-stu-id="ecc33-113">Child Elements</span></span>  
  
|<span data-ttu-id="ecc33-114">要素</span><span class="sxs-lookup"><span data-stu-id="ecc33-114">Element</span></span>|<span data-ttu-id="ecc33-115">説明</span><span class="sxs-lookup"><span data-stu-id="ecc33-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecc33-116">\<oidEntry ></span><span class="sxs-lookup"><span data-stu-id="ecc33-116">\<oidEntry></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="ecc33-117">ASN.1 OID をフレンドリ名にマップします。</span><span class="sxs-lookup"><span data-stu-id="ecc33-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ecc33-118">親要素</span><span class="sxs-lookup"><span data-stu-id="ecc33-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ecc33-119">要素</span><span class="sxs-lookup"><span data-stu-id="ecc33-119">Element</span></span>|<span data-ttu-id="ecc33-120">説明</span><span class="sxs-lookup"><span data-stu-id="ecc33-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ecc33-121">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="ecc33-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="ecc33-122">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="ecc33-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="ecc33-123">含まれています、`cryptographySettings`要素。</span><span class="sxs-lookup"><span data-stu-id="ecc33-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ecc33-124">例</span><span class="sxs-lookup"><span data-stu-id="ecc33-124">Example</span></span>  
 <span data-ttu-id="ecc33-125">次の例を使用する方法を示しています、  **\<oidMap >**要素をそのハッシュ アルゴリズムの実装に ripemd-160 ハッシュ アルゴリズムの OID のマッピングが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ecc33-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ecc33-126">参照</span><span class="sxs-lookup"><span data-stu-id="ecc33-126">See Also</span></span>  
 [<span data-ttu-id="ecc33-127">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="ecc33-127">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="ecc33-128">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="ecc33-128">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="ecc33-129">暗号サービス</span><span class="sxs-lookup"><span data-stu-id="ecc33-129">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="ecc33-130">暗号化クラスの設定</span><span class="sxs-lookup"><span data-stu-id="ecc33-130">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="ecc33-131">暗号化アルゴリズムへのオブジェクト ID の割り当て</span><span class="sxs-lookup"><span data-stu-id="ecc33-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
