---
title: "WIF 構成スキーマの規則"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e327b45ddd260d1a52066b5bf53e7114100ff45c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wif-configuration-schema-conventions"></a><span data-ttu-id="35fcf-102">WIF 構成スキーマの規則</span><span class="sxs-lookup"><span data-stu-id="35fcf-102">WIF Configuration Schema Conventions</span></span>
<span data-ttu-id="35fcf-103">このトピックでは、Windows Identity Foundation (WIF) 構成トピックを通して利用される規則について説明し、[\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) セクションと [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) セクションで利用されるいくつかの一般的な機能と属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="35fcf-103">This topic discusses conventions used throughout the Windows Identity Foundation (WIF) configuration topics and describes some common features and attributes used in the [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) and the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) sections.</span></span>  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a><span data-ttu-id="35fcf-104">モード</span><span class="sxs-lookup"><span data-stu-id="35fcf-104">Modes</span></span>  
 <span data-ttu-id="35fcf-105">WIF 構成要素の多くに `mode` 属性があります。</span><span class="sxs-lookup"><span data-stu-id="35fcf-105">Many of the WIF configuration elements have a `mode` attribute.</span></span> <span data-ttu-id="35fcf-106">この属性は通常、処理の特定の部分に使用されるクラスと、現在の要素の子要素として許可される構成要素を制御します。</span><span class="sxs-lookup"><span data-stu-id="35fcf-106">This attribute typically controls which class is used to do a particular part of the processing and which configuration elements are allowed as child elements of the current element.</span></span> <span data-ttu-id="35fcf-107">構成ファイルに含まれる要素がモード設定により無視される場合、構成エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="35fcf-107">A configuration error will be raised if elements that are included in the configuration file are ignored because of the mode settings.</span></span>  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a><span data-ttu-id="35fcf-108">TimeSpan 値</span><span class="sxs-lookup"><span data-stu-id="35fcf-108">Timespan Values</span></span>  
 <span data-ttu-id="35fcf-109"><xref:System.TimeSpan> は属性の種類として使用されます。許可される形式については、<xref:System.TimeSpan.Parse%28System.String%29> メソッドをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="35fcf-109">Where <xref:System.TimeSpan> is used as the type of an attribute, see the <xref:System.TimeSpan.Parse%28System.String%29> method to see the allowed format.</span></span> <span data-ttu-id="35fcf-110">この形式は、次の仕様に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="35fcf-110">This format conforms to the following specification.</span></span>  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 <span data-ttu-id="35fcf-111">たとえば、"30"、"30.00:00"、"30.00:00:00" はすべて 30 日を意味します。"00:05"、"00:05:00"、"0.00:05:00.00" はすべて 5 分を意味します。</span><span class="sxs-lookup"><span data-stu-id="35fcf-111">For example, "30", "30.00:00", "30.00:00:00" all mean 30 days; and "00:05", "00:05:00", "0.00:05:00.00" all mean 5 minutes.</span></span>  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a><span data-ttu-id="35fcf-112">証明書参照</span><span class="sxs-lookup"><span data-stu-id="35fcf-112">Certificate References</span></span>  
 <span data-ttu-id="35fcf-113">いくつかの要素は、`<certificateReference>` 要素を利用し、証明書参照を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="35fcf-113">Several elements take references to certificates using the `<certificateReference>` element.</span></span> <span data-ttu-id="35fcf-114">証明書を参照するとき、次の属性が利用できます。</span><span class="sxs-lookup"><span data-stu-id="35fcf-114">When referencing a certificate, the following attributes are available.</span></span>  
  
|||  
|-|-|  
|`storeLocation`|<span data-ttu-id="35fcf-115"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> 列挙の値: `CurrentUser` または `CurrentMachine`。</span><span class="sxs-lookup"><span data-stu-id="35fcf-115">A value of the <xref:System.Security.Cryptography.X509Certificates.StoreLocation> enumeration: `CurrentUser` or `CurrentMachine`.</span></span>|  
|`storeName`|<span data-ttu-id="35fcf-116"><xref:System.Security.Cryptography.X509Certificates.StoreName> 列挙の値。このコンテキストで最も有用なものは `My` と `TrustedPeople` です。</span><span class="sxs-lookup"><span data-stu-id="35fcf-116">A value of the <xref:System.Security.Cryptography.X509Certificates.StoreName> enumeration; the most useful for this context are `My` and `TrustedPeople`.</span></span>|  
|`x509FindType`|<span data-ttu-id="35fcf-117"><xref:System.Security.Cryptography.X509Certificates.X509FindType> 列挙の値。このコンテキストで最も有用なものは `FindBySubjectName` と `FindByThumbprint` です。</span><span class="sxs-lookup"><span data-stu-id="35fcf-117">A value of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> enumeration; the most useful for this context are `FindBySubjectName` and `FindByThumbprint`.</span></span> <span data-ttu-id="35fcf-118">エラーの可能性をなくすために、運用環境では `FindByThumbprint` 型を使用することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="35fcf-118">To eliminate the chance of error, it is recommended that the `FindByThumbprint` type be used in production environments.</span></span>|  
|`findValue`|<span data-ttu-id="35fcf-119">`x509FindType` 属性に基づき、証明書を検出するために使用される値。</span><span class="sxs-lookup"><span data-stu-id="35fcf-119">The value used to find the certificate, based on the `x509FindType` attribute.</span></span> <span data-ttu-id="35fcf-120">エラーの可能性をなくすために、運用環境では `FindByThumbprint` 型を使用することが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="35fcf-120">To eliminate the chance of error, it is recommended that the `FindByThumbprint` type be used in production environments.</span></span> <span data-ttu-id="35fcf-121">`FindByThumbPrint` が指定されると、この属性は、"97249e1a5fa6bee5e515b82111ef524a4c91583f" のような、16 進数文字列形式の証明書拇印である値を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="35fcf-121">When `FindByThumbPrint` is specified, this attribute takes a value that is the hexadecimal-string form of the certificate thumbprint; for example, "97249e1a5fa6bee5e515b82111ef524a4c91583f".</span></span>|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a><span data-ttu-id="35fcf-122">カスタム型の参照</span><span class="sxs-lookup"><span data-stu-id="35fcf-122">Custom Type References</span></span>  
 <span data-ttu-id="35fcf-123">いくつかの要素は、`type` 属性を利用し、カスタム型を参照します。</span><span class="sxs-lookup"><span data-stu-id="35fcf-123">Several elements reference custom types using the `type` attribute.</span></span> <span data-ttu-id="35fcf-124">この属性では、カスタム型の名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35fcf-124">This attribute should specify the name of the custom type.</span></span> <span data-ttu-id="35fcf-125">グローバル アセンブリ キャッシュ (GAC) から型を参照するには、厳密な名前を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35fcf-125">To reference a type from the Global Assembly Cache (GAC), a strong name should be used.</span></span> <span data-ttu-id="35fcf-126">Bin/ ディレクトリのアセンブリから型を参照するために、単純なアセンブリ修飾参照を利用できます。</span><span class="sxs-lookup"><span data-stu-id="35fcf-126">To reference a type from an assembly in the Bin/ directory, a simple assembly-qualified reference may be used.</span></span> <span data-ttu-id="35fcf-127">App_Code/ ディレクトリに定義されている型は、アセンブリ修飾のない型名を指定することでも参照できます。</span><span class="sxs-lookup"><span data-stu-id="35fcf-127">Types defined in the App_Code/ directory may also be referenced by simply specifying the type name with no qualifying assembly.</span></span>  
  
 <span data-ttu-id="35fcf-128">カスタム型は、指定された型から派生する必要があります。`public` の既定 (0 引数) コンストラクターを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35fcf-128">Custom types must be derived from the type specified and they must provide a `public` default (0 argument) constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35fcf-129">参照</span><span class="sxs-lookup"><span data-stu-id="35fcf-129">See Also</span></span>  
 [<span data-ttu-id="35fcf-130">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="35fcf-130">\<system.identityModel></span></span>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)  
 [<span data-ttu-id="35fcf-131">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="35fcf-131">\<system.identityModel.services></span></span>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
