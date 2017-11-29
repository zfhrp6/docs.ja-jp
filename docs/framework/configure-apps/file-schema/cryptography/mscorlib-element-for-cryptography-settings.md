---
title: "&lt;mscorlib&gt;暗号化設定の要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 992e62575dccae3f68df27fb7dd027dceab91ffc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltmscorlibgt-element-for-cryptography-settings"></a><span data-ttu-id="e775f-102">&lt;mscorlib&gt;暗号化設定の要素</span><span class="sxs-lookup"><span data-stu-id="e775f-102">&lt;mscorlib&gt; Element for Cryptography Settings</span></span>
<span data-ttu-id="e775f-103">含まれています、 [ \<cryptographySettings > 要素](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="e775f-103">Contains the [\<cryptographySettings> element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span></span>  
  
 <span data-ttu-id="e775f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e775f-104">\<configuration></span></span>  
<span data-ttu-id="e775f-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="e775f-105">\<mscorlib></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e775f-106">構文</span><span class="sxs-lookup"><span data-stu-id="e775f-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e775f-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e775f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e775f-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e775f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e775f-109">属性</span><span class="sxs-lookup"><span data-stu-id="e775f-109">Attributes</span></span>  
 <span data-ttu-id="e775f-110">なし。</span><span class="sxs-lookup"><span data-stu-id="e775f-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e775f-111">子要素</span><span class="sxs-lookup"><span data-stu-id="e775f-111">Child Elements</span></span>  
  
|<span data-ttu-id="e775f-112">要素</span><span class="sxs-lookup"><span data-stu-id="e775f-112">Element</span></span>|<span data-ttu-id="e775f-113">説明</span><span class="sxs-lookup"><span data-stu-id="e775f-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="e775f-114">暗号設定を含みます。</span><span class="sxs-lookup"><span data-stu-id="e775f-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e775f-115">親要素</span><span class="sxs-lookup"><span data-stu-id="e775f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e775f-116">要素</span><span class="sxs-lookup"><span data-stu-id="e775f-116">Element</span></span>|<span data-ttu-id="e775f-117">説明</span><span class="sxs-lookup"><span data-stu-id="e775f-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e775f-118">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="e775f-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e775f-119">例</span><span class="sxs-lookup"><span data-stu-id="e775f-119">Example</span></span>  
 <span data-ttu-id="e775f-120">次の例を使用する方法を示しています、  **\<mscorlib >**暗号化クラスを参照し、ランタイムを構成する要素。</span><span class="sxs-lookup"><span data-stu-id="e775f-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="e775f-121">文字列"RSA"を渡すことができますし、<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>メソッドを使用して、<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>を返すメソッドを`MyCryptoRSAClass`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e775f-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e775f-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e775f-122">See Also</span></span>  
 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>  
 <xref:System.Security.Cryptography>  
 [<span data-ttu-id="e775f-123">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="e775f-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="e775f-124">暗号化設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="e775f-124">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="e775f-125">暗号サービス</span><span class="sxs-lookup"><span data-stu-id="e775f-125">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="e775f-126">暗号化クラスの設定</span><span class="sxs-lookup"><span data-stu-id="e775f-126">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
