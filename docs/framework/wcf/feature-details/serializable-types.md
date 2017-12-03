---
title: "シリアル化可能な型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e368472db3bdca73661586821106174e13d4d24
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="serializable-types"></a><span data-ttu-id="15654-102">シリアル化可能な型</span><span class="sxs-lookup"><span data-stu-id="15654-102">Serializable Types</span></span>
<span data-ttu-id="15654-103">既定では、<xref:System.Runtime.Serialization.DataContractSerializer> は公開されている型をすべてシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="15654-103">By default, the <xref:System.Runtime.Serialization.DataContractSerializer> serializes all publicly visible types.</span></span> <span data-ttu-id="15654-104">その型の読み書き可能なパブリック プロパティおよびパブリック フィールドは、すべてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="15654-104">All public read/write properties and fields of the type are serialized.</span></span>  
  
 <span data-ttu-id="15654-105">既定の動作を変更するには、<xref:System.Runtime.Serialization.DataContractAttribute> 属性と <xref:System.Runtime.Serialization.DataMemberAttribute> 属性を型とメンバーに適用します。この機能は、使用するコントロールに型がない場合や属性を追加するように変更できない場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="15654-105">You can change the default behavior by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the types and members This feature can be useful in situations in which you have types that are not under your control and cannot be modified to add attributes.</span></span> <span data-ttu-id="15654-106"><xref:System.Runtime.Serialization.DataContractSerializer> は "マークされていない" 型を認識します。</span><span class="sxs-lookup"><span data-stu-id="15654-106">The <xref:System.Runtime.Serialization.DataContractSerializer> recognizes such "unmarked" types.</span></span>  
  
## <a name="serialization-defaults"></a><span data-ttu-id="15654-107">シリアル化の既定</span><span class="sxs-lookup"><span data-stu-id="15654-107">Serialization Defaults</span></span>  
 <span data-ttu-id="15654-108"><xref:System.Runtime.Serialization.DataContractAttribute> 属性と <xref:System.Runtime.Serialization.DataMemberAttribute> 属性を適用して、型とメンバーのシリアル化を明示的に制御またはカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="15654-108">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to explicitly control or customize the serialization of types and members.</span></span> <span data-ttu-id="15654-109">さらに、これらの属性をプライベート フィールドに適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="15654-109">In addition, you can apply these attributes to private fields.</span></span> <span data-ttu-id="15654-110">ただし、これらの属性でマークされていない型もシリアル化および逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="15654-110">However, even types that are not marked with these attributes are serialized and deserialized.</span></span> <span data-ttu-id="15654-111">次のルールと例外が適用されます。</span><span class="sxs-lookup"><span data-stu-id="15654-111">The following rules and exceptions apply:</span></span>  
  
-   <span data-ttu-id="15654-112"><xref:System.Runtime.Serialization.DataContractSerializer> は、新しく作成した型の既定のプロパティを使用して、属性のない型からデータ コントラクトを推論します。</span><span class="sxs-lookup"><span data-stu-id="15654-112">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract from types without attributes using the default properties of the newly created types.</span></span>  
  
-   <span data-ttu-id="15654-113">すべてのパブリック フィールドと、パブリック `get` メソッドおよび `set` メソッドを持つプロパティは、<xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> 属性をそのメンバーに適用しない限りシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="15654-113">All public fields, and properties with public `get` and `set` methods are serialized, unless you apply the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute to that member.</span></span>  
  
-   <span data-ttu-id="15654-114">シリアル化のセマンティクスは <xref:System.Xml.Serialization.XmlSerializer> に似ています。</span><span class="sxs-lookup"><span data-stu-id="15654-114">The serialization semantics are similar to those of the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
-   <span data-ttu-id="15654-115">マークされていない型では、パラメーターのないコンストラクターを持つパブリック型のみがシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="15654-115">In unmarked types, only public types with constructors that do not have parameters are serialized.</span></span> <span data-ttu-id="15654-116">このルールの例外として、<xref:System.Runtime.Serialization.ExtensionDataObject> インターフェイスとして使用される <xref:System.Runtime.Serialization.IExtensibleDataObject> があります。</span><span class="sxs-lookup"><span data-stu-id="15654-116">The exception to this rule is <xref:System.Runtime.Serialization.ExtensionDataObject> used with the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span>  
  
-   <span data-ttu-id="15654-117">読み取り専用フィールド、`get` メソッドまたは `set` メソッドのないプロパティ、内部またはプライベート `set` メソッドまたは `get` メソッドのあるプロパティはシリアル化されません。</span><span class="sxs-lookup"><span data-stu-id="15654-117">Read-only fields, properties without a `get` or `set` method, and properties with internal or private `set` or `get` methods are not serialized.</span></span> <span data-ttu-id="15654-118">そのようなプロパティは無視され、例外はスローされません。ただし、取得専用のコレクションの場合は除きます。</span><span class="sxs-lookup"><span data-stu-id="15654-118">Such properties are ignored and no exception is thrown, except in the case of get-only collections.</span></span>  
  
-   <span data-ttu-id="15654-119"><xref:System.Xml.Serialization.XmlSerializer> 属性 (`XmlElement`、`XmlAttribute`、`XmlIgnore`、`XmlInclude` など) は無視されます。</span><span class="sxs-lookup"><span data-stu-id="15654-119"><xref:System.Xml.Serialization.XmlSerializer> attributes (such as `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`, and so on) are ignored.</span></span>  
  
-   <span data-ttu-id="15654-120"><xref:System.Runtime.Serialization.DataContractAttribute> 属性を指定の型に適用しない場合は、シリアライザーは <xref:System.Runtime.Serialization.DataMemberAttribute> 属性が適用されるその型のすべてのメンバーを無視します。</span><span class="sxs-lookup"><span data-stu-id="15654-120">If you do not apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a given type, the serializer ignores any member in that type to which the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute is applied.</span></span>  
  
-   <span data-ttu-id="15654-121"><xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> プロパティは <xref:System.Runtime.Serialization.DataContractAttribute> 属性でマークされていない型でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="15654-121">The <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> property is supported in types not marked with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute.</span></span> <span data-ttu-id="15654-122">これには、マークされていない型での <xref:System.Runtime.Serialization.KnownTypeAttribute> 属性のサポートも含まれます。</span><span class="sxs-lookup"><span data-stu-id="15654-122">This includes support for the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on unmarked types.</span></span>  
  
-   <span data-ttu-id="15654-123">パブリック メンバー、プロパティ、またはフィールドのシリアル化のプロセスを "取り消す" には、<xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> 属性をそのメンバーに適用します。</span><span class="sxs-lookup"><span data-stu-id="15654-123">To "opt out" of the serialization process for public members, properties, or fields, apply the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute to that member.</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="15654-124">継承</span><span class="sxs-lookup"><span data-stu-id="15654-124">Inheritance</span></span>  
 <span data-ttu-id="15654-125">マークされていない型 (<xref:System.Runtime.Serialization.DataContractAttribute> 属性のない型) は、この属性を持つ型から継承できます。ただし、その反対はできません。つまり、マークされていない型から属性を持つ型を継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="15654-125">Unmarked types (types without the <xref:System.Runtime.Serialization.DataContractAttribute> attribute) can inherit from types that do have this attribute; however, the reverse is not permitted: types with the attribute cannot inherit from unmarked types.</span></span> <span data-ttu-id="15654-126">このルールは、主に以前のバージョンの [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] で書かれたコードとの下位互換性を保つために適用されます。</span><span class="sxs-lookup"><span data-stu-id="15654-126">This rule is enforced primarily to ensure backward compatibility with code written in earlier versions of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15654-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="15654-127">See Also</span></span>  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="15654-128">データ コントラクト シリアライザーでサポートされる型</span><span class="sxs-lookup"><span data-stu-id="15654-128">Types Supported by the Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
