---
title: "開発者の視点から見た ASP.NET Web サービスと WCF との比較"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6aa79e76bd81c0d56b30d4bac2edd4b9cbef6b33
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="3d058-102">開発者の視点から見た ASP.NET Web サービスと WCF との比較</span><span class="sxs-lookup"><span data-stu-id="3d058-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="3d058-103"> には ASP.NET 互換モードがあります。このモードにすると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションを ASP.NET Web サービスと同じようにプログラミングおよび構成し、動作を真似ることができます。</span><span class="sxs-lookup"><span data-stu-id="3d058-103"> has an ASP.NET compatibility mode option to enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="3d058-104">以下のセクションでは、ASP.NET Web サービスと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を、それぞれの技術を使ってアプリケーションを開発する視点から比較してみます。</span><span class="sxs-lookup"><span data-stu-id="3d058-104">The following sections compare ASP.NET Web services and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] based on what is required to develop applications using both technologies.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="3d058-105">データ表現</span><span class="sxs-lookup"><span data-stu-id="3d058-105">Data Representation</span></span>  
 <span data-ttu-id="3d058-106">ASP.NET で Web サービスを開発する場合、通常はまず、このサービスが使う複合データ型の定義から始めます。</span><span class="sxs-lookup"><span data-stu-id="3d058-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="3d058-107">ASP.NET は <xref:System.Xml.Serialization.XmlSerializer> を利用して、.NET Framework 型で表されたデータを XML 形式に変換してサービスとの間でやり取りしたり、XML 形式で受け取ったデータを .NET Framework オブジェクトに変換したりします。</span><span class="sxs-lookup"><span data-stu-id="3d058-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="3d058-108">ASP.NET サービスで使用する複合データ型を定義するには、<xref:System.Xml.Serialization.XmlSerializer> で XML 形式にシリアル化したり、XML 形式から逆シリアル化したりできる .NET Framework クラスの定義が必要です。</span><span class="sxs-lookup"><span data-stu-id="3d058-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="3d058-109">クラス定義は手で記述するほか、XML スキーマの型定義から生成することも可能です。それにはコマンド ライン上で実行する XML スキーマ/データ型サポート ユーティリティである xsd.exe を使います。</span><span class="sxs-lookup"><span data-stu-id="3d058-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>  
  
 <span data-ttu-id="3d058-110"><xref:System.Xml.Serialization.XmlSerializer> で XML 形式にシリアル化したり、XML 形式から逆シリアル化したりできる .NET Framework クラスを定義する場合に知っておくべき主な事項を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3d058-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>  
  
-   <span data-ttu-id="3d058-111">XML に変換されるのは、.NET Framework オブジェクトのパブリック フィールドおよびパブリック プロパティに限ります。</span><span class="sxs-lookup"><span data-stu-id="3d058-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>  
  
-   <span data-ttu-id="3d058-112">コレクション クラスのインスタンスを XML 形式にシリアル化できるのは、そのクラスが <xref:System.Collections.IEnumerable> または <xref:System.Collections.ICollection> インターフェイスを実装している場合に限ります。</span><span class="sxs-lookup"><span data-stu-id="3d058-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>  
  
-   <span data-ttu-id="3d058-113"><xref:System.Collections.IDictionary> インターフェイスを実装した、<xref:System.Collections.Hashtable> などのクラスを、XML 形式にシリアル化することはできません。</span><span class="sxs-lookup"><span data-stu-id="3d058-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>  
  
-   <span data-ttu-id="3d058-114"><xref:System.Xml.Serialization> 名前空間の属性型は、大部分が .NET Framework クラスやそのメンバーに追加可能であり、これにより、XML での当該クラスのインスタンスの表現方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>  
  
 <span data-ttu-id="3d058-115">通常、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションの開発も、複合型の定義から始めます。</span><span class="sxs-lookup"><span data-stu-id="3d058-115">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application development usually also begins with the definition of complex types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="3d058-116"> でも ASP.NET Web サービスと同じ .NET Framework 型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-116"> can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="3d058-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.Runtime.Serialization.DataContractAttribute> や <xref:System.Runtime.Serialization.DataMemberAttribute> を .NET Framework 型に追加して、ある型のインスタンスを XML にシリアル化できる旨や、当該型のどのフィールドやプロパティを実際にシリアル化できるのかを指定することができます。その例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="3d058-117">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>  
  
```  
//Example One:   
[DataContract]  
public class LineItem  
{  
    [DataMember]  
    public string ItemNumber;  
    [DataMember]  
    public decimal Quantity;  
    [DataMember]  
    public decimal UnitPrice;  
}  
  
//Example Two:   
public class LineItem  
{  
    [DataMember]  
    private string itemNumber;  
    [DataMember]  
    private decimal quantity;  
    [DataMember]  
    private decimal unitPrice;  
  
    public string ItemNumber  
    {  
      get  
      {  
          return this.itemNumber;  
      }  
  
      set  
      {  
          this.itemNumber = value;  
      }  
    }  
  
    public decimal Quantity  
    {  
        get  
        {  
            return this.quantity;  
        }  
  
        set  
        {  
            this.quantity = value;  
        }  
    }  
  
    public decimal UnitPrice  
    {  
      get  
      {  
          return this.unitPrice;  
      }  
  
      set  
      {  
          this.unitPrice = value;  
      }  
    }  
}  
  
//Example Three:   
public class LineItem  
{  
     private string itemNumber;  
     private decimal quantity;  
     private decimal unitPrice;  
  
     [DataMember]  
     public string ItemNumber  
     {  
       get  
       {  
          return this.itemNumber;  
       }  
  
       set  
       {  
           this.itemNumber = value;  
       }  
     }  
  
     [DataMember]  
     public decimal Quantity  
     {  
          get  
          {  
              return this.quantity;  
          }  
  
          set  
          {  
             this.quantity = value;  
          }  
     }  
  
     [DataMember]  
     public decimal UnitPrice  
     {  
          get  
          {  
              return this.unitPrice;  
          }  
  
          set  
          {  
              this.unitPrice = value;  
          }  
     }  
}  
```  
  
 <span data-ttu-id="3d058-118"><xref:System.Runtime.Serialization.DataContractAttribute> は、当該型の中にシリアル化可能なフィールドやプロパティがあることを示し、具体的にどのフィールドやプロパティをシリアル化できるかを <xref:System.Runtime.Serialization.DataMemberAttribute> で示します。</span><span class="sxs-lookup"><span data-stu-id="3d058-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="3d058-119"><xref:System.Runtime.Serialization.DataContractAttribute> はクラスにも構造体にも適用できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="3d058-120"><xref:System.Runtime.Serialization.DataMemberAttribute> はフィールドやプロパティに適用します。これはパブリックでもプライベートでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="3d058-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="3d058-121"><xref:System.Runtime.Serialization.DataContractAttribute> が適用された型のインスタンスのことを、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ではデータ コントラクトと呼びます。</span><span class="sxs-lookup"><span data-stu-id="3d058-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="3d058-122">これを XML 形式にシリアル化するには <xref:System.Runtime.Serialization.DataContractSerializer> を使います。</span><span class="sxs-lookup"><span data-stu-id="3d058-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="3d058-123"><xref:System.Runtime.Serialization.DataContractSerializer> を使う場合と、<xref:System.Xml.Serialization.XmlSerializer> および <xref:System.Xml.Serialization> 名前空間に定義された属性を使う場合の、主な違いを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="3d058-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>  
  
-   <span data-ttu-id="3d058-124"><xref:System.Xml.Serialization.XmlSerializer> や <xref:System.Xml.Serialization> 名前空間の属性は、XML スキーマで定義された有効な型であればどれにでも .NET Framework 型をマップできるようにするためのものです。これらを使うと、XML での型の表現方法を細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="3d058-125">これに対し、<xref:System.Runtime.Serialization.DataContractSerializer>、<xref:System.Runtime.Serialization.DataContractAttribute>、および <xref:System.Runtime.Serialization.DataMemberAttribute> の場合、XML での型の表現方法にはほとんど自由度がありません。</span><span class="sxs-lookup"><span data-stu-id="3d058-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="3d058-126">指定できるのは、名前空間と、型やフィールド、プロパティを XML で表す名前、フィールドやプロパティの XML における並び順だけです。</span><span class="sxs-lookup"><span data-stu-id="3d058-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>  
  
    ```  
    [DataContract(  
    Namespace="urn:Contoso:2006:January:29",  
    Name="LineItem")]  
    public class LineItem  
    {  
         [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]  
         public string itemNumber;  
         [DataMember(Name="Quantity",IsRequired=false,Order = 1)]  
         public decimal quantity;  
         [DataMember(Name="Price",IsRequired=false,Order = 2)]  
         public decimal unitPrice;  
    }  
    ```  
  
     <span data-ttu-id="3d058-127">上記以外の事項は、<xref:System.Runtime.Serialization.DataContractSerializer> に固定で組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="3d058-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
-   <span data-ttu-id="3d058-128"><xref:System.Runtime.Serialization.DataContractSerializer> の場合、型の XML での表現方法に自由度が小さく、したがってシリアル化のプロセスがあらかじめ大部分予測できるので、最適化が容易です。</span><span class="sxs-lookup"><span data-stu-id="3d058-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="3d058-129"><xref:System.Runtime.Serialization.DataContractSerializer> を使えば、性能が約 10% 向上するという現実的な利点があります。</span><span class="sxs-lookup"><span data-stu-id="3d058-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>  
  
-   <span data-ttu-id="3d058-130"><xref:System.Xml.Serialization.XmlSerializer> を使用する方法では、どのフィールドやプロパティを XML にシリアル化するかを属性で指定することはできませんが、<xref:System.Runtime.Serialization.DataMemberAttribute> の場合は <xref:System.Runtime.Serialization.DataContractSerializer> 属性で明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="3d058-131">このように、データ コントラクトとは、アプリケーションとの間でやり取りするデータ構造を明示した契約であると言うことができます。</span><span class="sxs-lookup"><span data-stu-id="3d058-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>  
  
-   <span data-ttu-id="3d058-132"><xref:System.Xml.Serialization.XmlSerializer> で XML 形式に変換できるのは、.NET オブジェクトのパブリック メンバーに限ります。一方 <xref:System.Runtime.Serialization.DataContractSerializer> は、アクセス修飾子にかかわらず、どのメンバーでも変換可能です。</span><span class="sxs-lookup"><span data-stu-id="3d058-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>  
  
-   <span data-ttu-id="3d058-133"><xref:System.Runtime.Serialization.DataContractSerializer> の場合、パブリックでないメンバーも XML に変換できるため、シリアル化できる .NET 型についての制約が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="3d058-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="3d058-134">特に、<xref:System.Collections.Hashtable> など、<xref:System.Collections.IDictionary> インターフェイスを実装した型が変換可能です。</span><span class="sxs-lookup"><span data-stu-id="3d058-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="3d058-135"><xref:System.Runtime.Serialization.DataContractSerializer> はさらに、既存の .NET 型のインスタンスを XML にシリアル化する場合でも、型定義を変更したり、ラッパーを定義したりする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="3d058-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>  
  
-   <span data-ttu-id="3d058-136"><xref:System.Runtime.Serialization.DataContractSerializer> はパブリックでないメンバーも変換できるため、完全に信頼できるコードからしか実行できないようになっています。<xref:System.Xml.Serialization.XmlSerializer> にはそのような制約がありません。</span><span class="sxs-lookup"><span data-stu-id="3d058-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="3d058-137">コードの完全信頼アクセス権限とは、当該マシン上のすべてのリソースにアクセスできる権限で、その確認には資格情報を使います。</span><span class="sxs-lookup"><span data-stu-id="3d058-137">The Full Trust code access permission give complete access to all resources on a machine that can be access using the credentials under which the code is executing.</span></span> <span data-ttu-id="3d058-138">他のリソースにも制限なくアクセスできるので、このようなコードの取り扱いには十分に注意しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="3d058-138">This options should be used with care as fully trusted code accesses all resources on your machine.</span></span>  
  
-   <span data-ttu-id="3d058-139"><xref:System.Runtime.Serialization.DataContractSerializer> にはバージョン管理の機能がいくつか組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="3d058-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>  
  
    -   <span data-ttu-id="3d058-140"><xref:System.Runtime.Serialization.DataMemberAttribute> には <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> プロパティがあります。旧バージョンにはなかったメンバーを追加した場合に、そのプロパティを false とすれば、当該データ コントラクトの新バージョンを扱うアプリケーションが、旧バージョンのデータも扱えるようになります。</span><span class="sxs-lookup"><span data-stu-id="3d058-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>  
  
    -   <span data-ttu-id="3d058-141">データ コントラクトに <xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスを実装すると、<xref:System.Runtime.Serialization.DataContractSerializer> は、新バージョンのデータ コントラクトで定義されたメンバーを、旧バージョンのコントラクトを扱うアプリケーション経由で受け渡しできるようになります。</span><span class="sxs-lookup"><span data-stu-id="3d058-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>  
  
 <span data-ttu-id="3d058-142">以上のようにさまざまな違いがありますが、<xref:System.Xml.Serialization.XmlSerializer> で既定の設定を使用して型をシリアル化したものは、XML の名前空間を明示的に定義してあれば、<xref:System.Runtime.Serialization.DataContractSerializer> で型をシリアル化したものと意味的に同等です。</span><span class="sxs-lookup"><span data-stu-id="3d058-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="3d058-143">次のクラスは、属性が <xref:System.Xml.Serialization.XmlSerializer>、<xref:System.Runtime.Serialization.DataContractAttribute> のどちらのシリアライザーでも変換の対象となり、最終的に得られる XML も意味的に同等です。</span><span class="sxs-lookup"><span data-stu-id="3d058-143">The following class, which has attributes for use with both of the serializers, are translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>  
  
```  
[Serializable]  
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]  
[DataContract(Namespace="urn:Contoso:2006:January:29")]  
public class LineItem  
{  
     [DataMember]  
     public string ItemNumber;  
     [DataMember]  
     public decimal Quantity;  
     [DataMember]  
     public decimal UnitPrice;  
}  
```  
  
 <span data-ttu-id="3d058-144">Windows ソフトウェア開発キット (SDK) というコマンド ライン ツールが含まれています、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。ASP.NET Web サービスで使用される xsd.exe ツールと同様に Svcutil.exe は、XML スキーマから .NET データ型の定義を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="3d058-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="3d058-145"><xref:System.Runtime.Serialization.DataContractSerializer> が XML スキーマで定義された形式の XML を出力できる場合、型はデータ コントラクトの形に変換されます。そうでなければ、<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="3d058-145">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="3d058-146">Svcutil.exe に `/dataContractOnly` スイッチを指定して起動すると、データ コントラクトから XML スキーマを生成できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-146">The tool, Svcutil.exe, can also be made to generate XML Schema from data contracts using its `/dataContractOnly` switch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d058-147">ASP.NET Web サービスは <xref:System.Xml.Serialization.XmlSerializer> を使うようになっています。ASP.NET 互換モードの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが ASP.NET Web サービスの動作を真似るようになっていますが、<xref:System.Xml.Serialization.XmlSerializer> を使わなければならないわけではありません。</span><span class="sxs-lookup"><span data-stu-id="3d058-147">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode makes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="3d058-148">必要であれば ASP.NET 互換モードでも <xref:System.Runtime.Serialization.DataContractSerializer> も使えるようになっています。</span><span class="sxs-lookup"><span data-stu-id="3d058-148">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="3d058-149">サービスの開発</span><span class="sxs-lookup"><span data-stu-id="3d058-149">Service Development</span></span>  
 <span data-ttu-id="3d058-150">ASP.NET を使用してサービスを開発する場合、通常は <xref:System.Web.Services.WebService> 属性をクラスに追加し、<xref:System.Web.Services.WebMethodAttribute> を当該クラスのサービスに対する操作メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="3d058-150">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>  
  
```  
[WebService]  
public class Service : T:System.Web.Services.WebService  
{  
    [WebMethod]  
    public string Echo(string input)   
    {  
       return input;  
    }  
}  
```  
  
 <span data-ttu-id="3d058-151">ASP.NET 2.0 では、<xref:System.Web.Services.WebService> 属性や <xref:System.Web.Services.WebMethodAttribute> 属性をクラスではなくインターフェイスに追加し、そのインターフェイスを実装するクラスを記述する、という方法も使えるようになりました。</span><span class="sxs-lookup"><span data-stu-id="3d058-151">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>  
  
```  
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <span data-ttu-id="3d058-152"><xref:System.Web.Services.WebService> 属性を持つインターフェイスは、サービスによって実行される操作のコントラクトを構成し、またそれをさまざまなクラスで再利用することによって、同じコントラクトをさまざまな方法で実装できるので、このオプションの使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3d058-152">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="3d058-153">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] エンドポイントをいくつか定義することにより提供されます。</span><span class="sxs-lookup"><span data-stu-id="3d058-153">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is provided by defining one or more [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoints.</span></span> <span data-ttu-id="3d058-154">エンドポイントは、アドレス、バインディング、サービス コントラクトで定義します。</span><span class="sxs-lookup"><span data-stu-id="3d058-154">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="3d058-155">アドレスとは、サービスが配備された場所のことです。</span><span class="sxs-lookup"><span data-stu-id="3d058-155">The address defines where the service is located.</span></span> <span data-ttu-id="3d058-156">バインディングはサービスとの通信方法を表します。</span><span class="sxs-lookup"><span data-stu-id="3d058-156">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="3d058-157">サービス コントラクトとは、サービスが実行できる操作の定義のことです。</span><span class="sxs-lookup"><span data-stu-id="3d058-157">The service contract defines the operations that the service can perform.</span></span>  
  
 <span data-ttu-id="3d058-158">サービス コントラクトは通常、インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> および <xref:System.ServiceModel.OperationContractAttribute> を追加して定義します。</span><span class="sxs-lookup"><span data-stu-id="3d058-158">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>  
  
```  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <span data-ttu-id="3d058-159"><xref:System.ServiceModel.ServiceContractAttribute> は、当該インターフェイスが [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス コントラクトを定義することを表します。また、<xref:System.ServiceModel.OperationContractAttribute> は、インターフェイスのどのメソッドが (存在する場合) サービス コントラクトの操作を定義しているかを表します。</span><span class="sxs-lookup"><span data-stu-id="3d058-159">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>  
  
 <span data-ttu-id="3d058-160">このようにして定義されたサービス コントラクトをクラスとして実装します。サービス コントラクトを定義するインターフェイスを実装するクラスという形で記述します。</span><span class="sxs-lookup"><span data-stu-id="3d058-160">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>  
  
```  
public class Service : IEcho  
{  
    public string Echo(string input)  
    {  
       return input;  
    }  
}  
```  
  
 <span data-ttu-id="3d058-161">サービス コントラクトを実装したクラスは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ではサービスとして参照できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-161">A class that implements a service contract is referred to as a service type in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="3d058-162">次に、アドレスとバインディングを、サービス型と関連付けます。</span><span class="sxs-lookup"><span data-stu-id="3d058-162">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="3d058-163">これは通常、構成ファイルを直接編集するか、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に収録されている構成エディターを使って行います。</span><span class="sxs-lookup"><span data-stu-id="3d058-163">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="3d058-164">構成ファイルの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="3d058-164">Here is an example of a configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
     <system.serviceModel>  
      <services>  
      <service name="Service ">  
       <endpoint   
        address="EchoService"  
        binding="basicHttpBinding"  
        contract="IEchoService "/>  
      </service>  
      </services>  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="3d058-165">バインディングは、アプリケーションとの通信に使う一連のプロトコルを表します。</span><span class="sxs-lookup"><span data-stu-id="3d058-165">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="3d058-166">一般的なシステム指定のバインディングを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="3d058-166">The following table lists the system-provided bindings that represent common options.</span></span>  
  
|<span data-ttu-id="3d058-167">名前</span><span class="sxs-lookup"><span data-stu-id="3d058-167">Name</span></span>|<span data-ttu-id="3d058-168">目的</span><span class="sxs-lookup"><span data-stu-id="3d058-168">Purpose</span></span>|  
|----------|-------------|  
|<span data-ttu-id="3d058-169">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3d058-169">BasicHttpBinding</span></span>|<span data-ttu-id="3d058-170">WS-BasicProfile 1.1 および Basic Security Profile 1.0 に対応した Web サービスやクライアントとの相互運用性。</span><span class="sxs-lookup"><span data-stu-id="3d058-170">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|  
|<span data-ttu-id="3d058-171">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3d058-171">WSHttpBinding</span></span>|<span data-ttu-id="3d058-172">HTTP 上の WS-* プロトコルに対応した Web サービスやクライアントとの相互運用性。</span><span class="sxs-lookup"><span data-stu-id="3d058-172">Interoperability with Web services and clients that support the WS-* protocols over HTTP.</span></span>|  
|<span data-ttu-id="3d058-173">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3d058-173">WSDualHttpBinding</span></span>|<span data-ttu-id="3d058-174">双方向 HTTP 通信。最初のメッセージの受信者は送信元に直接は応答せず、代わりに、WS-* プロトコルに準拠した HTTP で、ある期間にわたって任意の数の応答を送信することができます。</span><span class="sxs-lookup"><span data-stu-id="3d058-174">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-* protocols.</span></span>|  
|<span data-ttu-id="3d058-175">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="3d058-175">WSFederationBinding</span></span>|<span data-ttu-id="3d058-176">HTTP 通信。サービスのリソースに対するアクセスを、明示的に指定された資格情報プロバイダーによって発行された証明書に基づいて制御することができます。</span><span class="sxs-lookup"><span data-stu-id="3d058-176">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|  
|<span data-ttu-id="3d058-177">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="3d058-177">NetTcpBinding</span></span>|<span data-ttu-id="3d058-178">ネットワーク全体に分散する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ソフトウェア エンティティ間の、安全性や信頼性を確保した高速通信。</span><span class="sxs-lookup"><span data-stu-id="3d058-178">Secure, reliable, high-performance communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities across a network.</span></span>|  
|<span data-ttu-id="3d058-179">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="3d058-179">NetNamedPipeBinding</span></span>|<span data-ttu-id="3d058-180">同一コンピューター上の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ソフトウェア エンティティ間の、安全性や信頼性を確保した高速通信。</span><span class="sxs-lookup"><span data-stu-id="3d058-180">Secure, reliable, high-performance communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities on the same machine.</span></span>|  
|<span data-ttu-id="3d058-181">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="3d058-181">NetMsmqBinding</span></span>|<span data-ttu-id="3d058-182">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ソフトウェア エンティティ間の、MSMQ を使用した通信。</span><span class="sxs-lookup"><span data-stu-id="3d058-182">Communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities by using MSMQ.</span></span>|  
|<span data-ttu-id="3d058-183">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="3d058-183">MsmqIntegrationBinding</span></span>|<span data-ttu-id="3d058-184">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ソフトウェアと他のソフトウェア エンティティ間の、MSMQ を使用した通信。</span><span class="sxs-lookup"><span data-stu-id="3d058-184">Communication between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entity and another software entity by using MSMQ.</span></span>|  
|<span data-ttu-id="3d058-185">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="3d058-185">NetPeerTcpBinding</span></span>|<span data-ttu-id="3d058-186">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ソフトウェア エンティティ間の、Windows ピアツーピア ネットワークを使用した通信。</span><span class="sxs-lookup"><span data-stu-id="3d058-186">Communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities by using Windows Peer-to-Peer Networking.</span></span>|  
  
 <span data-ttu-id="3d058-187">システム指定のバインディングである <xref:System.ServiceModel.BasicHttpBinding> には、ASP.NET Web サービスが対応している一連のプロトコルが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="3d058-187">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="3d058-188">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーション用の独自バインディングは、バインド要素クラスのコレクションとして定義し、各クラスに個々のプロトコルを実装して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で使えるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="3d058-188">Custom bindings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications are easily defined as collections of the binding element classes that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses to implement individual protocols.</span></span> <span data-ttu-id="3d058-189">追加のプロトコルを表す、新しいバインド要素を記述することも可能です。</span><span class="sxs-lookup"><span data-stu-id="3d058-189">New binding elements can be written to represent additional protocols.</span></span>  
  
 <span data-ttu-id="3d058-190">サービス型の内部的な動作は、動作を表すクラス群のプロパティで調整できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-190">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="3d058-191">次の例で、<xref:System.ServiceModel.ServiceBehaviorAttribute> クラスは、サービス型がマルチスレッド処理されることを指定しています。</span><span class="sxs-lookup"><span data-stu-id="3d058-191">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 <span data-ttu-id="3d058-192"><xref:System.ServiceModel.ServiceBehaviorAttribute> など、属性として定義された動作もあります。</span><span class="sxs-lookup"><span data-stu-id="3d058-192">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="3d058-193">これに対し、管理者がプロパティを設定できる動作は、アプリケーションの構成ファイルで変更することができます。</span><span class="sxs-lookup"><span data-stu-id="3d058-193">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>  
  
 <span data-ttu-id="3d058-194">サービス型のプログラムの記述には、多くの場合 <xref:System.ServiceModel.OperationContext> クラスを使います。</span><span class="sxs-lookup"><span data-stu-id="3d058-194">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="3d058-195">静的プロパティである <xref:System.ServiceModel.OperationContext.Current%2A> を介して、実行コンテキストに関する情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3d058-195">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="3d058-196"><xref:System.ServiceModel.OperationContext> の使い方は、<xref:System.Web.HttpContext> クラスや <xref:System.EnterpriseServices.ContextUtil> クラスと同様です。</span><span class="sxs-lookup"><span data-stu-id="3d058-196"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="3d058-197">ホスト</span><span class="sxs-lookup"><span data-stu-id="3d058-197">Hosting</span></span>  
 <span data-ttu-id="3d058-198">ASP.NET Web サービスは、コンパイルしてクラス ライブラリ アセンブリの形になっています。</span><span class="sxs-lookup"><span data-stu-id="3d058-198">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="3d058-199">サービス ファイルという、拡張子が .asmx のファイルの `@ WebService` ディレクティブに、サービスの実行コードが組み込まれたクラスと、これを収容するアセンブリが定義されています。</span><span class="sxs-lookup"><span data-stu-id="3d058-199">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 <span data-ttu-id="3d058-200">サービス ファイルをインターネット インフォメーション サービス (IIS) の ASP.NET アプリケーション ルート、アセンブリをアプリケーション ルートのサブディレクトリ \bin 以下にコピーすると、</span><span class="sxs-lookup"><span data-stu-id="3d058-200">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="3d058-201">このサービス ファイルの URL (Uniform Resource Locator) でアプリケーションにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="3d058-201">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="3d058-202"> サービスは、IIS 5.1 や 6.0 の他、IIS 7.0 の一部として提供される Windows プロセス アクティブ化サービス (WAS) や、.NET アプリケーション上でホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="3d058-202"> services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="3d058-203">ただし IIS 5.1/6.0 の場合、通信トランスポート プロトコルは HTTP に限ります。</span><span class="sxs-lookup"><span data-stu-id="3d058-203">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>  
  
 <span data-ttu-id="3d058-204">IIS 5.1/6.0 または WAS 上でサービスをホストする手順を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="3d058-204">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>  
  
1.  <span data-ttu-id="3d058-205">サービス型をコンパイルしてクラス ライブラリ アセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="3d058-205">Compile the service type into a class library assembly.</span></span>  
  
2.  <span data-ttu-id="3d058-206">拡張子を .svc としたサービス ファイルを作り、サービス型を `@ ServiceHost` ディレクティブで次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="3d058-206">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  <span data-ttu-id="3d058-207">サービス ファイルを仮想ディレクトリにコピーし、アセンブリをその仮想ディレクトリの \bin サブディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="3d058-207">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>  
  
4.  <span data-ttu-id="3d058-208">構成ファイルを仮想ディレクトリに、Web.config という名前でコピーします。</span><span class="sxs-lookup"><span data-stu-id="3d058-208">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>  
  
 <span data-ttu-id="3d058-209">するとアプリケーションには、アプリケーション ルートに置いたサービス ファイルの URL でアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="3d058-209">The application is then accessible by using the URL of the service file in the application root.</span></span>  
  
 <span data-ttu-id="3d058-210">.NET アプリケーション上で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストする場合は、サービス型をコンパイルしてクラス ライブラリ アセンブリを生成し、これをアプリケーションが参照できるようにします。アプリケーション側では、<xref:System.ServiceModel.ServiceHost> クラスを使って、サービスを管理できるようプログラムを記述します。</span><span class="sxs-lookup"><span data-stu-id="3d058-210">To host a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="3d058-211">サービスを管理する基本的なプログラムの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="3d058-211">The following is an example of the basic programming required:</span></span>  
  
```  
string httpBaseAddress = "http://www.contoso.com:8000/";  
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";  
  
Uri httpBaseAddressUri = new Uri(httpBaseAddress);  
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);  
  
Uri[] baseAdresses = new Uri[] {   
 httpBaseAddressUri,  
 tcpBaseAddressUri};  
  
using(ServiceHost host = new ServiceHost(  
typeof(Service), //"Service" is the name of the service type baseAdresses))  
{  
     host.Open();  
  
     […] //Wait to receive messages  
     host.Close();  
}  
```  
  
 <span data-ttu-id="3d058-212">この例では <xref:System.ServiceModel.ServiceHost> の構築時にトランスポート プロトコルに対してアドレスを指定しています。</span><span class="sxs-lookup"><span data-stu-id="3d058-212">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="3d058-213">このアドレスをベース アドレスと呼びます。</span><span class="sxs-lookup"><span data-stu-id="3d058-213">These addresses are referred to as base addresses.</span></span>  
  
 <span data-ttu-id="3d058-214">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのエンドポイントは、エンドポイントのホストに設定されたベース アドレスから見た相対アドレスで表します。</span><span class="sxs-lookup"><span data-stu-id="3d058-214">The address provided for any endpoint of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="3d058-215">ホストではトランスポート プロトコルごとに 1 つベース アドレスを設定できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-215">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="3d058-216">上記の構成ファイルの構成例では、エンドポイントに対して選択された <xref:System.ServiceModel.BasicHttpBinding> はトランスポート プロトコルとして HTTP を使用しているので、エンドポイント `EchoService` のアドレスは、HTTP に対して設定されたベース アドレスを基準としたものになります。</span><span class="sxs-lookup"><span data-stu-id="3d058-216">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="3d058-217">上記の例に挙げたホストの場合、HTTP ベース アドレスは http://www.contoso.com:8000/ です。</span><span class="sxs-lookup"><span data-stu-id="3d058-217">In the case of the host in the preceding example, the HTTP base address is http://www.contoso.com:8000/.</span></span> <span data-ttu-id="3d058-218">なお、IIS や WAS 上でホストされているサービスの場合、ベース アドレスはサービス ファイルの URL になります。</span><span class="sxs-lookup"><span data-stu-id="3d058-218">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>  
  
 <span data-ttu-id="3d058-219">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を ASP.NET 互換モードで動かせるのは、IIS や WAS 上でホストされていて、トランスポート プロトコルとしてもっぱら HTTP を使うサービスに限ります。</span><span class="sxs-lookup"><span data-stu-id="3d058-219">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode option.</span></span> <span data-ttu-id="3d058-220">ASP.NET 互換モードは、次の 2 つの手順で切り替えます。</span><span class="sxs-lookup"><span data-stu-id="3d058-220">Turning that option on requires the following steps.</span></span>  
  
1.  <span data-ttu-id="3d058-221">プログラムの開発者は、サービス型に <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 属性を追加し、ASP.NET 互換モードに切り替えることができる、または切り替えることが必須である旨の指定をしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d058-221">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>  
  
    ```  
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(  
          RequirementsMode=AspNetCompatbilityRequirementsMode.Require)]  
    public class DerivativesCalculatorServiceType: IDerivativesCalculator  
    ```  
  
2.  <span data-ttu-id="3d058-222">管理者は、アプリケーションが ASP.NET 互換モードで動作するよう、次のように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d058-222">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>  
  
    ```xml  
    <configuration>  
         <system.serviceModel>  
          <services>  
          […]  
          </services>  
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="3d058-223"> アプリケーションは、サービス ファイルの拡張子として .svc ではなく .asmx を使用するように構成することも可能です。</span><span class="sxs-lookup"><span data-stu-id="3d058-223"> applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>  
  
    ```xml  
    <system.web>  
         <compilation>  
          <compilation debug="true">  
          <buildProviders>  
           <remove extension=".asmx"/>  
           <add extension=".asmx"   
            type="System.ServiceModel.ServiceBuildProvider,   
            Systemm.ServiceModel,   
            Version=3.0.0.0,   
            Culture=neutral,   
            PublicKeyToken=b77a5c561934e089" />  
          </buildProviders>  
          </compilation>  
         </compilation>  
    </system.web>  
    ```  
  
     <span data-ttu-id="3d058-224">このように構成すると、.asmx サービス ファイルの URL を使用するようクライアント側を変更しなくても、サービスは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用するようになります。</span><span class="sxs-lookup"><span data-stu-id="3d058-224">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="client-development"></a><span data-ttu-id="3d058-225">クライアント開発</span><span class="sxs-lookup"><span data-stu-id="3d058-225">Client Development</span></span>  
 <span data-ttu-id="3d058-226">ASP.NET Web サービスのクライアントの開発にはコマンド ライン ツール WSDL.exe を使用します.asmx ファイルの URL を入力として指定します。</span><span class="sxs-lookup"><span data-stu-id="3d058-226">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="3d058-227">対応するツールによって提供される[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]は[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="3d058-227">The corresponding tool provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="3d058-228">これは、サービス コントラクトおよび [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント クラスの定義から、コード モジュールを生成します。</span><span class="sxs-lookup"><span data-stu-id="3d058-228">It generates a code module with the definition of the service contract and the definition of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class.</span></span> <span data-ttu-id="3d058-229">また、サービスのアドレスとバインディングを指定して、構成ファイルを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3d058-229">It also generates a configuration file with the address and binding of the service.</span></span>  
  
 <span data-ttu-id="3d058-230">リモート サービスのクライアントを開発する場合、通常は、非同期パターンに従ってプログラムを記述するようお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3d058-230">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="3d058-231">WSDL.exe ツールは、特段の指定をしなくても、同期パターンと非同期パターンを使ったコードをそれぞれ生成します。</span><span class="sxs-lookup"><span data-stu-id="3d058-231">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="3d058-232">によって生成されたコード、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)いずれかのパターンを提供できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-232">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="3d058-233">特に指定しなければ同期パターン用です。</span><span class="sxs-lookup"><span data-stu-id="3d058-233">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="3d058-234">`/async` スイッチを指定して実行すれば、生成されるコードは非同期パターン用になります。</span><span class="sxs-lookup"><span data-stu-id="3d058-234">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>  
  
 <span data-ttu-id="3d058-235">ASP.NET の WSDL.exe で生成した [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント クラスの名前が、Svcutil.exe で生成した [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント クラスの名前と一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="3d058-235">There is no guarantee that names in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="3d058-236">特に、<xref:System.Xml.Serialization.XmlSerializer> でシリアル化したクラスのプロパティ名は、Svcutil.exe で生成した場合 "Property" という接頭辞が付きますが、WSDL.exe の場合はそうなりません。</span><span class="sxs-lookup"><span data-stu-id="3d058-236">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>  
  
## <a name="message-representation"></a><span data-ttu-id="3d058-237">メッセージ表現</span><span class="sxs-lookup"><span data-stu-id="3d058-237">Message Representation</span></span>  
 <span data-ttu-id="3d058-238">ASP.NET Web サービスとやり取りする SOAP メッセージのヘッダーはカスタマイズ可能です。</span><span class="sxs-lookup"><span data-stu-id="3d058-238">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="3d058-239"><xref:System.Web.Services.Protocols.SoapHeader> の派生クラスでヘッダーの構造を定義し、<xref:System.Web.Services.Protocols.SoapHeaderAttribute> でヘッダーが存在することを指定します。</span><span class="sxs-lookup"><span data-stu-id="3d058-239">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>  
  
```  
public class SomeProtocol : SoapHeader  
{  
     public long CurrentValue;  
     public long Total;  
}  
  
[WebService]  
public interface IEcho  
{  
     SomeProtocol ProtocolHeader  
     {  
      get;  
     set;  
     }  
  
     [WebMethod]  
     [SoapHeader("ProtocolHeader")]  
     string PlaceOrders(PurchaseOrderType order);  
}  
  
public class Service: WebService, IEcho  
{  
     private SomeProtocol protocolHeader;  
  
     public SomeProtocol ProtocolHeader  
     {  
         get  
         {  
              return this.protocolHeader;  
         }  
  
         set  
         {  
              this.protocolHeader = value;  
         }  
     }  
  
     string PlaceOrders(PurchaseOrderType order)  
     {  
         long currentValue = this.protocolHeader.CurrentValue;  
     }  
}  
```  
  
 <span data-ttu-id="3d058-240">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、サービスとやり取りする SOAP メッセージの構造を記述する、<xref:System.ServiceModel.MessageContractAttribute>、<xref:System.ServiceModel.MessageHeaderAttribute>、および <xref:System.ServiceModel.MessageBodyMemberAttribute> という属性があります。</span><span class="sxs-lookup"><span data-stu-id="3d058-240">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>  
  
```  
[DataContract]  
public class SomeProtocol  
{  
     [DataMember]  
     public long CurrentValue;  
     [DataMember]  
     public long Total;  
}  
  
[DataContract]  
public class Item  
{  
     [DataMember]  
     public string ItemNumber;  
     [DataMember]  
     public decimal Quantity;  
     [DataMember]  
     public decimal UnitPrice;  
}  
  
[MessageContract]  
public class ItemMesage  
{  
     [MessageHeader]  
     public SomeProtocol ProtocolHeader;  
     [MessageBody]  
     public Item Content;  
}  
  
[ServiceContract]  
public interface IItemService  
{  
     [OperationContract]  
     public void DeliverItem(ItemMessage itemMessage);  
}  
```  
  
 <span data-ttu-id="3d058-241">この構文でメッセージ構造を明示的に記述できますが、ASP.NET Web サービスのコードからメッセージ構造を導くことも可能です。</span><span class="sxs-lookup"><span data-stu-id="3d058-241">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="3d058-242">ASP.NET の構文では、メッセージ ヘッダーは上記の例の `ProtocolHeader` のようにサービスのプロパティとして表現されますが、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ではメッセージのプロパティとしてより厳密に表現できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-242">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="3d058-243">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ではさらに、エンドポイントの構成にメッセージ ヘッダーを追加することも可能です。</span><span class="sxs-lookup"><span data-stu-id="3d058-243">Also, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows message headers to be added to the configuration of endpoints.</span></span>  
  
```xml  
<service name="Service ">  
     <endpoint   
      address="EchoService"  
      binding="basicHttpBinding"  
      contract="IEchoService ">  
      <headers>  
      <dsig:X509Certificate   
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">  
       ...  
      </dsig:X509Certificate>  
      </headers>  
     </endpoint>  
</service>  
```  
  
 <span data-ttu-id="3d058-244">この方法では、クライアントやサービスのコード内で、基盤となるプロトコル ヘッダーを参照しなくても済みます。エンドポイントが適切に構成されているので、ヘッダーがメッセージ中に取り込まれるからです。</span><span class="sxs-lookup"><span data-stu-id="3d058-244">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>  
  
## <a name="service-description"></a><span data-ttu-id="3d058-245">サービスの説明</span><span class="sxs-lookup"><span data-stu-id="3d058-245">Service Description</span></span>  
 <span data-ttu-id="3d058-246">WSDL で記述したクエリを HTTP GET 要求として発行して、ASP.NET Web サービスの .asmx ファイルを取得しようとすると、ASP.NET は WSDL によるサービス記述を生成し、</span><span class="sxs-lookup"><span data-stu-id="3d058-246">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="3d058-247">要求に対する応答として返します。</span><span class="sxs-lookup"><span data-stu-id="3d058-247">It returns that WSDL as the response to the request.</span></span>  
  
 <span data-ttu-id="3d058-248">ASP.NET 2.0 では、サービスが Web Services-Interoperability Organization (WS-I) の Basic Profile 1.1 に準拠していることを検証し、その旨を WSDL による記述に追加できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="3d058-248">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="3d058-249">この処理には、`ConformsTo` 属性の `EmitConformanceClaims` および <xref:System.Web.Services.WebServiceBindingAttribute> パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="3d058-249">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="3d058-250">ASP.NET が WSDL で生成したサービス記述はカスタマイズ可能です。</span><span class="sxs-lookup"><span data-stu-id="3d058-250">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="3d058-251"><xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> の派生クラスを作成し、WSDL による記述に項目を追加する、という形でカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="3d058-251">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>  
  
 <span data-ttu-id="3d058-252">WSDL で記述したクエリを HTTP GET 要求として発行して、IIS 5.1/6.0 または WAS でホストされていて HTTP エンドポイントを持つ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの .svc ファイルを取得しようとすると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は WSDL によるサービス記述を生成して返します。</span><span class="sxs-lookup"><span data-stu-id="3d058-252">Issuing an HTTP GET request with the query WSDL for the .svc file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to respond with WSDL to describe the service.</span></span> <span data-ttu-id="3d058-253">httpGetEnabled が true に設定されている場合は、WSDL で記述したクエリを HTTP GET 要求として、.NET アプリケーション上でホストされているサービスの HTTP ベース アドレスに発行しても同じ効力があります。</span><span class="sxs-lookup"><span data-stu-id="3d058-253">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>  
  
 <span data-ttu-id="3d058-254">一方、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、WS-MetadataExchange 要求に対しても、WSDL によるサービス記述を生成して返します。</span><span class="sxs-lookup"><span data-stu-id="3d058-254">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="3d058-255">ASP.NET Web サービスには、WS-MetadataExchange 要求に応答する機能がありません。</span><span class="sxs-lookup"><span data-stu-id="3d058-255">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>  
  
 <span data-ttu-id="3d058-256">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が WSDL で生成したサービス記述は広範なカスタマイズが可能です。</span><span class="sxs-lookup"><span data-stu-id="3d058-256">The WSDL that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates can be extensively customized.</span></span> <span data-ttu-id="3d058-257"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> クラスには、WSDL による記述をカスタマイズするための機能がいくつか組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="3d058-257">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="3d058-258">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] も、WSDL による記述を生成する代わりに、所定の URL に置いた静的な WSDL ファイルを使用するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-258">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>  
  
```xml  
<behaviors>  
     <behavior name="DescriptionBehavior">  
     <metadataPublishing   
      enableMetadataExchange="true"   
      enableGetWsdl="true"   
      enableHelpPage="true"   
      metadataLocation=  
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>  
     </behavior>  
</behaviors>  
```  
  
## <a name="exception-handling"></a><span data-ttu-id="3d058-259">例外処理</span><span class="sxs-lookup"><span data-stu-id="3d058-259">Exception Handling</span></span>  
 <span data-ttu-id="3d058-260">ASP.NET Web サービスでは、処理できない例外が発生すると、SOAP エラーとしてクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="3d058-260">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="3d058-261">また、<xref:System.Web.Services.Protocols.SoapException> クラスのインスタンスを明示的にスローして、クライアント側に SOAP エラーの詳しい状況を通知し、より適切に管理させることも可能です。</span><span class="sxs-lookup"><span data-stu-id="3d058-261">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>  
  
 <span data-ttu-id="3d058-262">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスでは、処理できない例外が発生しても SOAP エラーとしてクライアントに返すことはありません。重要な情報が不用意に表示され、第三者に漏洩するのを防ぐためです。</span><span class="sxs-lookup"><span data-stu-id="3d058-262">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="3d058-263">ただしデバッグ目的で、このような例外をクライアントに返すように設定することは可能です。</span><span class="sxs-lookup"><span data-stu-id="3d058-263">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>  
  
 <span data-ttu-id="3d058-264">SOAP エラーをクライアントに返す場合、データ コントラクト型を汎用型 <xref:System.ServiceModel.FaultException%601> のインスタンスとしてキャストし、これをスローする方法が使えます。</span><span class="sxs-lookup"><span data-stu-id="3d058-264">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="3d058-265">また、操作に <xref:System.ServiceModel.FaultContractAttribute> 属性を追加して、操作で生じうるエラーを指定する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="3d058-265">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>  
  
```  
[DataContract]  
public class MathFault  
{   
     [DataMember]  
     public string operation;  
     [DataMember]  
     public string problemType;  
}  
  
[ServiceContract]  
public interface ICalculator  
{  
     [OperationContract]  
     [FaultContract(typeof(MathFault))]  
     int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="3d058-266">これにより、サービスで発生する可能性のあるエラーが WSDL の形で公開されます。クライアント側の開発者は、当該操作によりどのようなエラーが生じうるかをあらかじめ予測し、catch ブロック内に適切な処理を組み込んでおくことができます。</span><span class="sxs-lookup"><span data-stu-id="3d058-266">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>  
  
```  
try  
{  
     result = client.Divide(value1, value2);  
}  
catch (FaultException<MathFault> e)  
{  
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "  
  + e.Detail.operation   
  + ". Problem: "   
  + e.Detail.problemType);  
}  
```  
  
## <a name="state-management"></a><span data-ttu-id="3d058-267">状態管理</span><span class="sxs-lookup"><span data-stu-id="3d058-267">State Management</span></span>  
 <span data-ttu-id="3d058-268">ASP.NET Web サービスの実装には <xref:System.Web.Services.WebService> の派生クラスを使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="3d058-268">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>  
  
```  
public class Service : WebService, IEcho  
{  
  
 public string Echo(string input)  
 {  
  return input;  
 }  
}  
```  
  
 <span data-ttu-id="3d058-269">この場合、基本クラス <xref:System.Web.Services.WebService> に定義された Context プロパティを使って、<xref:System.Web.HttpContext> オブジェクトにアクセスすることになります。</span><span class="sxs-lookup"><span data-stu-id="3d058-269">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="3d058-270"><xref:System.Web.HttpContext> オブジェクトには、アプリケーションやセッションの状態情報をそれぞれ更新、取得する、Application プロパティ、Session プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="3d058-270">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>  
  
 <span data-ttu-id="3d058-271">ASP.NET では、<xref:System.Web.HttpContext> の Session プロパティでアクセスするセッション状態情報の、実際の格納場所を細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-271">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="3d058-272">格納場所としては、クッキー内、データベース内、稼動中のサーバーのメモリ上、状態管理用の特別なサーバーのメモリ上があり、</span><span class="sxs-lookup"><span data-stu-id="3d058-272">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="3d058-273">サービスの構成ファイルで指定します。</span><span class="sxs-lookup"><span data-stu-id="3d058-273">The choice is made in the service’s configuration file.</span></span>  
  
 <span data-ttu-id="3d058-274">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、状態管理用に拡張可能なオブジェクトがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="3d058-274">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides extensible objects for state management.</span></span> <span data-ttu-id="3d058-275">いずれも <xref:System.ServiceModel.IExtensibleObject%601> を実装しています。</span><span class="sxs-lookup"><span data-stu-id="3d058-275">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="3d058-276">中でも重要な拡張可能オブジェクトは、<xref:System.ServiceModel.ServiceHostBase> および <xref:System.ServiceModel.InstanceContext> です。</span><span class="sxs-lookup"><span data-stu-id="3d058-276">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="3d058-277">`ServiceHostBase` を使用すると、同一ホスト上の全サービス型のあらゆるインスタンスからアクセスできる状態を管理できます。一方、`InstanceContext` を使用すると、同じサービス型のインスタンス内で実行されるコードからアクセスできる状態を管理できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-277">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>  
  
 <span data-ttu-id="3d058-278">次の例で、サービス型 `TradingSystem` には <xref:System.ServiceModel.ServiceBehaviorAttribute> という属性があります。同じ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント インスタンスからの呼び出しはすべて、同じサービス型のインスタンスに転送されることを表します。</span><span class="sxs-lookup"><span data-stu-id="3d058-278">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client instance are routed to the same instance of the service type.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class TradingSystem: ITradingService  
```  
  
 <span data-ttu-id="3d058-279">次のクラス `DealData` に定義されている状態には、同じサービス型のインスタンス内で実行されるどのコードからでもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3d058-279">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>  
  
```  
internal class DealData: IExtension<InstanceContext>  
{  
 public string DealIdentifier = null;  
 public Trade[] Trades = null;  
}  
```  
  
 <span data-ttu-id="3d058-280">サービス コントラクトの操作のいずれかを実装するサービス型のコードでは、状態オブジェクト `DealData` を、当該サービス型の現在のインスタンスに関する状態として追加することができます。</span><span class="sxs-lookup"><span data-stu-id="3d058-280">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>  
  
```  
string ITradingService.BeginDeal()  
{  
 string dealIdentifier = Guid.NewGuid().ToString();  
 DealData state = new DealData(dealIdentifier);  
 OperationContext.Current.InstanceContext.Extensions.Add(state);  
 return dealIdentifier;  
}  
```  
  
 <span data-ttu-id="3d058-281">この状態オブジェクトは、サービス コントラクトの他の操作を実装するコードから取得、更新できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-281">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>  
  
```  
void ITradingService.AddTrade(Trade trade)  
{  
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();  
 dealData.AddTrade(trade);  
}  
```  
  
 <span data-ttu-id="3d058-282">ASP.NET では <xref:System.Web.HttpContext> クラスで管理する状態情報の実際の格納場所を制御できますが、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の場合、少なくとも初期バージョンのままでは、まったく制御ができません。</span><span class="sxs-lookup"><span data-stu-id="3d058-282">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="3d058-283">これも [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの ASP.NET 互換モードを推奨する理由の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="3d058-283">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="3d058-284">このような制御が不可欠な応用の場合、ASP.NET 互換モードにすれば、ASP.NET と同様に <xref:System.Web.HttpContext> クラスの機能を活用できるばかりでなく、<xref:System.Web.HttpContext> クラスで管理する状態情報の実際の格納場所も制御できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-284">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>  
  
## <a name="security"></a><span data-ttu-id="3d058-285">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3d058-285">Security</span></span>  
 <span data-ttu-id="3d058-286">ASP.NET Web サービスのセキュリティ保全の手順は、IIS アプリケーションのセキュリティ保全の手順と同じです。</span><span class="sxs-lookup"><span data-stu-id="3d058-286">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="3d058-287">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションは IIS に限らずどんな .NET 実行可能ファイル上でも動作するので、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションのセキュリティ保全の手順も IIS の機能に依存しないものにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d058-287">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can be hosted not only within IIS but also within any .NET executable, the options for securing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="3d058-288">しかし ASP.NET Web サービスが提供する機能は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスからも、ASP.NET 互換モードで動作していれば利用できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-288">However, the facilities provided for ASP.NET Web services are also available for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-authentication"></a><span data-ttu-id="3d058-289">セキュリティ : 認証</span><span class="sxs-lookup"><span data-stu-id="3d058-289">Security: Authentication</span></span>  
 <span data-ttu-id="3d058-290">IIS にはアプリケーションへのアクセス制御機能が組み込まれており、匿名アクセスの他、Windows 認証、ダイジェスト認証、基本認証、.NET パスポート認証など、さまざまな認証モードを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="3d058-290">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="3d058-291">Windows 認証は、ASP.NET Web サービスへのアクセス制御に使えます。</span><span class="sxs-lookup"><span data-stu-id="3d058-291">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="3d058-292">しかし [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションを IIS 上でホストする場合、アプリケーションへの匿名アクセスを許可するように IIS を構成し、認証処理は [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 自身で、Windows 認証その他により行えるようにしなければなりません。</span><span class="sxs-lookup"><span data-stu-id="3d058-292">However, when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="3d058-293">他の認証方法としては、ユーザー名トークン、X.509 証明書、SAML トークン、CardSpace カードなどが組み込まれていますが、独自の認証機構を定義することも可能です。</span><span class="sxs-lookup"><span data-stu-id="3d058-293">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>  
  
### <a name="security-impersonation"></a><span data-ttu-id="3d058-294">セキュリティ : 偽装</span><span class="sxs-lookup"><span data-stu-id="3d058-294">Security: Impersonation</span></span>  
 <span data-ttu-id="3d058-295">ASP.NET Web サービスは ASP.NET の ID 要素を使用して、あるユーザーに偽装することができます。あらかじめ設定した特定のユーザーでなくても、要求に資格情報が添えられていれば、その要求元ユーザーに偽装できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-295">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="3d058-296">ASP.NET 互換モードで動作する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションでは、この要素を使って偽装を構成できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-296">That element can be used to configure impersonation in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications running in ASP.NET compatibility mode.</span></span>  
  
 <span data-ttu-id="3d058-297">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、特定のユーザーに偽装する、独自の ID 要素を設定できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="3d058-297">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="3d058-298">また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のクライアント側とサービス側で、別々に偽装を構成できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-298">Also, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="3d058-299">クライアント側では、要求を送信する現在のユーザーに偽装する構成が可能です。</span><span class="sxs-lookup"><span data-stu-id="3d058-299">Clients can be configured to impersonate the current user when they transmit requests.</span></span>  
  
```xml  
<behaviors>  
     <behavior name="DerivativesCalculatorClientBehavior">  
      <clientCredentials>  
      <windows allowedImpersonationLevel="Impersonation"/>  
      </clientCredentials>  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="3d058-300">サービス側では、現在の要求と共に提供された資格情報のユーザーに偽装するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-300">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public void Receive(Message input)  
```  
  
### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="3d058-301">セキュリティ : アクセス制御リストによる承認</span><span class="sxs-lookup"><span data-stu-id="3d058-301">Security: Authorization using Access Control Lists</span></span>  
 <span data-ttu-id="3d058-302">アクセス制御リスト (ACL) を使って .asmx ファイルへのアクセスを制限できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-302">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="3d058-303">しかし、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の .svc ファイルに対しては、ASP.NET 互換モードでない限り、ACL でアクセス制限することはできません。</span><span class="sxs-lookup"><span data-stu-id="3d058-303">However, ACLs on [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .svc files are ignored except in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-role-based-authorization"></a><span data-ttu-id="3d058-304">セキュリティ : ロール ベースの承認</span><span class="sxs-lookup"><span data-stu-id="3d058-304">Security: Role-based Authorization</span></span>  
 <span data-ttu-id="3d058-305">IIS の Windows 認証オプションを、ASP.NET 構成言語の承認要素と組み合わせて使用すると、ASP.NET Web サービスに対し、各ユーザーが属する Windows グループに基づくロール ベースの承認機構を提供できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-305">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="3d058-306">ASP.NET 2.0 には、より汎用的なロール ベースの承認機構である、ロール プロバイダーが導入されました。</span><span class="sxs-lookup"><span data-stu-id="3d058-306">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>  
  
 <span data-ttu-id="3d058-307">ロール プロバイダーとは、ユーザーが割り当てられたロールに関する問い合わせを行う、基本インターフェイスを実装したクラス群です。各ロール プロバイダーには、さまざまな情報源から必要な情報を取得する手段が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="3d058-307">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="3d058-308">ASP.NET 2.0 には、Microsoft SQL Server データベースからロールの割り当てを検索できるロール プロバイダーと、Windows Server 2003 承認マネージャーから検索できるロール プロバイダーがあります。</span><span class="sxs-lookup"><span data-stu-id="3d058-308">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>  
  
 <span data-ttu-id="3d058-309">.NET アプリケーションでは、ロール プロバイダーの機構は ASP.NET と独立に使われています。これは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションも同様です。</span><span class="sxs-lookup"><span data-stu-id="3d058-309">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="3d058-310">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーション用の構成例を以下に示します。このように、ASP.NET のロール プロバイダーの使い方は、<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> で選択できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-310">The following sample configuration for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
```xml  
<system.serviceModel>  
     <services>  
         <service name="Service.ResourceAccessServiceType"   
             behaviorConfiguration="ServiceBehavior">  
             <endpoint   
              address="ResourceAccessService"   
              binding="wsHttpBinding"   
              contract="Service.IResourceAccessContract"/>  
         </service>  
     </services>  
     <behaviors>  
       <behavior name="ServiceBehavior">  
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>  
      </behavior>  
     </behaviors>  
</system.serviceModel>  
```  
  
### <a name="security-claims-based-authorization"></a><span data-ttu-id="3d058-311">セキュリティ : クレーム ベースの承認</span><span class="sxs-lookup"><span data-stu-id="3d058-311">Security: Claims-based Authorization</span></span>  
 <span data-ttu-id="3d058-312">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に導入された革新的な機能の 1 つで、保護されたリソースへのアクセスを、クレーム ベースで承認するというものです。</span><span class="sxs-lookup"><span data-stu-id="3d058-312">One of the most important innovations of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="3d058-313">クレームは、型、権限、および値で構成されます。たとえば、運転免許証を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="3d058-313">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="3d058-314">ここには所持者に関する誕生日などの情報 (ここでいう「クレーム」) が記載されています。</span><span class="sxs-lookup"><span data-stu-id="3d058-314">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="3d058-315">つまり、クレームの型は「誕生日」、値は運転者の実際の誕生日です。</span><span class="sxs-lookup"><span data-stu-id="3d058-315">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="3d058-316">また、クレームの権限は、所持者がこの値に対してできることを表します。</span><span class="sxs-lookup"><span data-stu-id="3d058-316">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="3d058-317">誕生日について言えば、所持者はこの情報を「見る」ことはできますが、「書き換える」ことはできません。</span><span class="sxs-lookup"><span data-stu-id="3d058-317">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="3d058-318">クレーム ベースの承認は、ロール ベースの承認を包含する概念です。というのも、ロールはクレームの 1 つの型であると考えることができるからです。</span><span class="sxs-lookup"><span data-stu-id="3d058-318">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>  
  
 <span data-ttu-id="3d058-319">クレーム ベースの承認では、一連のクレームを操作のアクセス要求と比較し、その結果に応じてアクセスを許可または拒否します。</span><span class="sxs-lookup"><span data-stu-id="3d058-319">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="3d058-320">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、クレーム ベースの承認を実行するクラスも、`ServiceAuthorizationManager` の <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> プロパティで指定します。</span><span class="sxs-lookup"><span data-stu-id="3d058-320">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="3d058-321">クレーム ベースの承認を行うクラスは、<xref:System.ServiceModel.ServiceAuthorizationManager> を継承し、`AccessCheck()` メソッドだけをオーバーライドして定義します。</span><span class="sxs-lookup"><span data-stu-id="3d058-321">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="3d058-322"> は、このメソッドを、サービスの操作が起動されたときに呼び出します。該当するユーザーのクレームを <xref:System.ServiceModel.OperationContext> プロパティに設定した、`ServiceSecurityContext.AuthorizationContext` オブジェクトを引数として渡します。</span><span class="sxs-lookup"><span data-stu-id="3d058-322"> calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="3d058-323"> は、提示されたセキュリティ トークンからユーザーに関するクレームを抽出、アセンブルし、要求された操作を許可してもよいかどうかを評価します。</span><span class="sxs-lookup"><span data-stu-id="3d058-323"> does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>  
  
 <span data-ttu-id="3d058-324">どのようなセキュリティ トークンからでも自動的にクレームをアセンブルできることが、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の革新的な技術です。これにより、認証機構と完全に独立して、クレーム ベースの承認を行うコードを実装できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="3d058-324">That [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="3d058-325">これに対し、ACL やロール ベースの承認は、Windows 認証と密に関連し合っています。</span><span class="sxs-lookup"><span data-stu-id="3d058-325">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>  
  
### <a name="security-confidentiality"></a><span data-ttu-id="3d058-326">セキュリティ : 機密性</span><span class="sxs-lookup"><span data-stu-id="3d058-326">Security: Confidentiality</span></span>  
 <span data-ttu-id="3d058-327">ASP.NET Web サービスとの間でやり取りするメッセージの機密性は、トランスポート層で、IIS 上のアプリケーションが Secure Hypertext Transfer Protocol (HTTPS) を使うように構成することによって確保します。</span><span class="sxs-lookup"><span data-stu-id="3d058-327">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="3d058-328">IIS 上でホストされている [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションについても同様です。</span><span class="sxs-lookup"><span data-stu-id="3d058-328">The same can be done for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications hosted within IIS.</span></span> <span data-ttu-id="3d058-329">しかし、IIS 以外でホストされている [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションも、安全なトランスポート プロトコルを使うように構成できます。</span><span class="sxs-lookup"><span data-stu-id="3d058-329">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="3d058-330">さらに [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションは、メッセージを転送前に WS-Security プロトコルにより保護するように構成することも可能です。</span><span class="sxs-lookup"><span data-stu-id="3d058-330">More important, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="3d058-331">メッセージの本体を WS-Security で保護することにより、最終送信先に到達するまでの中継ノードで機密が洩れないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="3d058-331">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>  
  
## <a name="globalization"></a><span data-ttu-id="3d058-332">グローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="3d058-332">Globalization</span></span>  
 <span data-ttu-id="3d058-333">ASP.NET 構成言語では、個々のサービスごとにカルチャを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="3d058-333">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="3d058-334">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でこの設定ができるのは、ASP.NET 互換モードの場合に限ります。</span><span class="sxs-lookup"><span data-stu-id="3d058-334">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="3d058-335">ASP.NET 互換モードでない [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをローカライズするためには、サービス型をコンパイルしてカルチャごとのアセンブリを生成し、エンドポイントもカルチャごとのアセンブリそれぞれについて用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d058-335">To localize a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d058-336">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d058-336">See Also</span></span>  
 [<span data-ttu-id="3d058-337">WCF ベースの目的で使用されている標準を ASP.NET Web サービスとの比較</span><span class="sxs-lookup"><span data-stu-id="3d058-337">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
