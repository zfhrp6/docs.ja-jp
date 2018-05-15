---
title: 開発者の視点から見た ASP.NET Web サービスと WCF との比較
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: fcf2d204d9d59a29024ff09d92be2a7b9339fce9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="04cf2-102">開発者の視点から見た ASP.NET Web サービスと WCF との比較</span><span class="sxs-lookup"><span data-stu-id="04cf2-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>
<span data-ttu-id="04cf2-103">Windows Communication Foundation (WCF) では、WCF アプリケーションをプログラミングおよび ASP.NET Web サービスのように構成を有効にして、その動作を模倣する ASP.NET 互換モード オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-103">Windows Communication Foundation (WCF) has an ASP.NET compatibility mode option to enable WCF applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="04cf2-104">次のセクションでは、ASP.NET Web サービスを比較し、WCF が両方のテクノロジを使用してアプリケーションを開発するための要件に基づいています。</span><span class="sxs-lookup"><span data-stu-id="04cf2-104">The following sections compare ASP.NET Web services and WCF based on what is required to develop applications using both technologies.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="04cf2-105">データ表現</span><span class="sxs-lookup"><span data-stu-id="04cf2-105">Data Representation</span></span>  
 <span data-ttu-id="04cf2-106">ASP.NET で Web サービスを開発する場合、通常はまず、このサービスが使う複合データ型の定義から始めます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="04cf2-107">ASP.NET は <xref:System.Xml.Serialization.XmlSerializer> を利用して、.NET Framework 型で表されたデータを XML 形式に変換してサービスとの間でやり取りしたり、XML 形式で受け取ったデータを .NET Framework オブジェクトに変換したりします。</span><span class="sxs-lookup"><span data-stu-id="04cf2-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="04cf2-108">ASP.NET サービスで使用する複合データ型を定義するには、<xref:System.Xml.Serialization.XmlSerializer> で XML 形式にシリアル化したり、XML 形式から逆シリアル化したりできる .NET Framework クラスの定義が必要です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="04cf2-109">クラス定義は手で記述するほか、XML スキーマの型定義から生成することも可能です。それにはコマンド ライン上で実行する XML スキーマ/データ型サポート ユーティリティである xsd.exe を使います。</span><span class="sxs-lookup"><span data-stu-id="04cf2-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>  
  
 <span data-ttu-id="04cf2-110"><xref:System.Xml.Serialization.XmlSerializer> で XML 形式にシリアル化したり、XML 形式から逆シリアル化したりできる .NET Framework クラスを定義する場合に知っておくべき主な事項を次に示します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>  
  
-   <span data-ttu-id="04cf2-111">XML に変換されるのは、.NET Framework オブジェクトのパブリック フィールドおよびパブリック プロパティに限ります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>  
  
-   <span data-ttu-id="04cf2-112">コレクション クラスのインスタンスを XML 形式にシリアル化できるのは、そのクラスが <xref:System.Collections.IEnumerable> または <xref:System.Collections.ICollection> インターフェイスを実装している場合に限ります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>  
  
-   <span data-ttu-id="04cf2-113"><xref:System.Collections.IDictionary> インターフェイスを実装した、<xref:System.Collections.Hashtable> などのクラスを、XML 形式にシリアル化することはできません。</span><span class="sxs-lookup"><span data-stu-id="04cf2-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>  
  
-   <span data-ttu-id="04cf2-114"><xref:System.Xml.Serialization> 名前空間の属性型は、大部分が .NET Framework クラスやそのメンバーに追加可能であり、これにより、XML での当該クラスのインスタンスの表現方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>  
  
 <span data-ttu-id="04cf2-115">WCF アプリケーションの開発通常も開始複合型の定義を使用します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-115">WCF application development usually also begins with the definition of complex types.</span></span> <span data-ttu-id="04cf2-116">ASP.NET Web サービスと同じ .NET Framework の型を使用するのには、WCF を作成できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-116">WCF can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="04cf2-117">WCF<xref:System.Runtime.Serialization.DataContractAttribute>と<xref:System.Runtime.Serialization.DataMemberAttribute>型のインスタンスは、XML、およびどの特定のフィールドまたはプロパティの型をシリアル化する、次のサンプル コードに示すようにシリアル化されることを示すために .NET Framework の型に追加できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-117">The WCF<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="04cf2-118"><xref:System.Runtime.Serialization.DataContractAttribute> は、当該型の中にシリアル化可能なフィールドやプロパティがあることを示し、具体的にどのフィールドやプロパティをシリアル化できるかを <xref:System.Runtime.Serialization.DataMemberAttribute> で示します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="04cf2-119"><xref:System.Runtime.Serialization.DataContractAttribute> はクラスにも構造体にも適用できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="04cf2-120"><xref:System.Runtime.Serialization.DataMemberAttribute> はフィールドやプロパティに適用します。これはパブリックでもプライベートでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="04cf2-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="04cf2-121">ある型のインスタンス、<xref:System.Runtime.Serialization.DataContractAttribute>に適用されるそれらと呼ばれます WCF でのデータ コントラクトします。</span><span class="sxs-lookup"><span data-stu-id="04cf2-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in WCF.</span></span> <span data-ttu-id="04cf2-122">これを XML 形式にシリアル化するには <xref:System.Runtime.Serialization.DataContractSerializer> を使います。</span><span class="sxs-lookup"><span data-stu-id="04cf2-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="04cf2-123"><xref:System.Runtime.Serialization.DataContractSerializer> を使う場合と、<xref:System.Xml.Serialization.XmlSerializer> および <xref:System.Xml.Serialization> 名前空間に定義された属性を使う場合の、主な違いを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>  
  
-   <span data-ttu-id="04cf2-124"><xref:System.Xml.Serialization.XmlSerializer> や <xref:System.Xml.Serialization> 名前空間の属性は、XML スキーマで定義された有効な型であればどれにでも .NET Framework 型をマップできるようにするためのものです。これらを使うと、XML での型の表現方法を細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="04cf2-125">これに対し、<xref:System.Runtime.Serialization.DataContractSerializer>、<xref:System.Runtime.Serialization.DataContractAttribute>、および <xref:System.Runtime.Serialization.DataMemberAttribute> の場合、XML での型の表現方法にはほとんど自由度がありません。</span><span class="sxs-lookup"><span data-stu-id="04cf2-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="04cf2-126">指定できるのは、名前空間と、型やフィールド、プロパティを XML で表す名前、フィールドやプロパティの XML における並び順だけです。</span><span class="sxs-lookup"><span data-stu-id="04cf2-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>  
  
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
  
     <span data-ttu-id="04cf2-127">上記以外の事項は、<xref:System.Runtime.Serialization.DataContractSerializer> に固定で組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="04cf2-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
-   <span data-ttu-id="04cf2-128"><xref:System.Runtime.Serialization.DataContractSerializer> の場合、型の XML での表現方法に自由度が小さく、したがってシリアル化のプロセスがあらかじめ大部分予測できるので、最適化が容易です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="04cf2-129"><xref:System.Runtime.Serialization.DataContractSerializer> を使えば、性能が約 10% 向上するという現実的な利点があります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>  
  
-   <span data-ttu-id="04cf2-130"><xref:System.Xml.Serialization.XmlSerializer> を使用する方法では、どのフィールドやプロパティを XML にシリアル化するかを属性で指定することはできませんが、<xref:System.Runtime.Serialization.DataMemberAttribute> の場合は <xref:System.Runtime.Serialization.DataContractSerializer> 属性で明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="04cf2-131">このように、データ コントラクトとは、アプリケーションとの間でやり取りするデータ構造を明示した契約であると言うことができます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>  
  
-   <span data-ttu-id="04cf2-132"><xref:System.Xml.Serialization.XmlSerializer> で XML 形式に変換できるのは、.NET オブジェクトのパブリック メンバーに限ります。一方 <xref:System.Runtime.Serialization.DataContractSerializer> は、アクセス修飾子にかかわらず、どのメンバーでも変換可能です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>  
  
-   <span data-ttu-id="04cf2-133"><xref:System.Runtime.Serialization.DataContractSerializer> の場合、パブリックでないメンバーも XML に変換できるため、シリアル化できる .NET 型についての制約が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="04cf2-134">特に、<xref:System.Collections.Hashtable> など、<xref:System.Collections.IDictionary> インターフェイスを実装した型が変換可能です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="04cf2-135"><xref:System.Runtime.Serialization.DataContractSerializer> はさらに、既存の .NET 型のインスタンスを XML にシリアル化する場合でも、型定義を変更したり、ラッパーを定義したりする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="04cf2-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>  
  
-   <span data-ttu-id="04cf2-136"><xref:System.Runtime.Serialization.DataContractSerializer> はパブリックでないメンバーも変換できるため、完全に信頼できるコードからしか実行できないようになっています。<xref:System.Xml.Serialization.XmlSerializer> にはそのような制約がありません。</span><span class="sxs-lookup"><span data-stu-id="04cf2-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="04cf2-137">コードの完全な信頼アクセス許可は、コードを実行している資格情報を使用してアクセスできるコンピューター上のすべてのリソースを完全なアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-137">The Full Trust code access permission gives complete access to all resources on a machine that can be accessed using the credentials under which the code is executing.</span></span> <span data-ttu-id="04cf2-138">完全に信頼されるコード、コンピューター上のすべてのリソースにアクセスすると、注意してこのオプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-138">This option should be used with care as fully trusted code accesses all resources on your machine.</span></span>  
  
-   <span data-ttu-id="04cf2-139"><xref:System.Runtime.Serialization.DataContractSerializer> にはバージョン管理の機能がいくつか組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="04cf2-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>  
  
    -   <span data-ttu-id="04cf2-140"><xref:System.Runtime.Serialization.DataMemberAttribute> には <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> プロパティがあります。旧バージョンにはなかったメンバーを追加した場合に、そのプロパティを false とすれば、当該データ コントラクトの新バージョンを扱うアプリケーションが、旧バージョンのデータも扱えるようになります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>  
  
    -   <span data-ttu-id="04cf2-141">データ コントラクトに <xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスを実装すると、<xref:System.Runtime.Serialization.DataContractSerializer> は、新バージョンのデータ コントラクトで定義されたメンバーを、旧バージョンのコントラクトを扱うアプリケーション経由で受け渡しできるようになります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>  
  
 <span data-ttu-id="04cf2-142">以上のようにさまざまな違いがありますが、<xref:System.Xml.Serialization.XmlSerializer> で既定の設定を使用して型をシリアル化したものは、XML の名前空間を明示的に定義してあれば、<xref:System.Runtime.Serialization.DataContractSerializer> で型をシリアル化したものと意味的に同等です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="04cf2-143">次のクラスは、シリアライザーの両方で使用するための属性を持ちは、同じ意味を持つ XML に変換、<xref:System.Xml.Serialization.XmlSerializer>および、 <xref:System.Runtime.Serialization.DataContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="04cf2-143">The following class, which has attributes for use with both of the serializers, is translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>  
  
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
  
 <span data-ttu-id="04cf2-144">Windows ソフトウェア開発キット (SDK) というコマンド ライン ツールが含まれています、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="04cf2-145">ASP.NET Web サービスで使用される xsd.exe ツールと同様に Svcutil.exe は、XML スキーマから .NET データ型の定義を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-145">Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="04cf2-146"><xref:System.Runtime.Serialization.DataContractSerializer> が XML スキーマで定義された形式の XML を出力できる場合、型はデータ コントラクトの形に変換されます。そうでなければ、<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-146">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="04cf2-147">Svcutil.exe から生成することも、XML スキーマ データ コントラクトを使用してその`dataContractOnly`スイッチします。</span><span class="sxs-lookup"><span data-stu-id="04cf2-147">Svcutil.exe can also generate an XML schema from data contracts by using its `dataContractOnly` switch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04cf2-148">ASP.NET Web サービスを使用して、 <xref:System.Xml.Serialization.XmlSerializer>、WCF の ASP.NET 互換モードは、ASP.NET Web サービスの動作を模倣する WCF サービス、ASP.NET 互換性オプションが制限していない 1 つを使用して、<xref:System.Xml.Serialization.XmlSerializer>です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-148">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and WCF ASP.NET compatibility mode makes WCF services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="04cf2-149">必要であれば ASP.NET 互換モードでも <xref:System.Runtime.Serialization.DataContractSerializer> も使えるようになっています。</span><span class="sxs-lookup"><span data-stu-id="04cf2-149">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="04cf2-150">サービスの開発</span><span class="sxs-lookup"><span data-stu-id="04cf2-150">Service Development</span></span>  
 <span data-ttu-id="04cf2-151">ASP.NET を使用してサービスを開発する場合、通常は <xref:System.Web.Services.WebService> 属性をクラスに追加し、<xref:System.Web.Services.WebMethodAttribute> を当該クラスのサービスに対する操作メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-151">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>  
  
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
  
 <span data-ttu-id="04cf2-152">ASP.NET 2.0 では、<xref:System.Web.Services.WebService> 属性や <xref:System.Web.Services.WebMethodAttribute> 属性をクラスではなくインターフェイスに追加し、そのインターフェイスを実装するクラスを記述する、という方法も使えるようになりました。</span><span class="sxs-lookup"><span data-stu-id="04cf2-152">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>  
  
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
  
 <span data-ttu-id="04cf2-153"><xref:System.Web.Services.WebService> 属性を持つインターフェイスは、サービスによって実行される操作のコントラクトを構成し、またそれをさまざまなクラスで再利用することによって、同じコントラクトをさまざまな方法で実装できるので、このオプションの使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="04cf2-153">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="04cf2-154">WCF サービスは、1 つまたは複数の WCF エンドポイントの定義によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-154">A WCF service is provided by defining one or more WCF endpoints.</span></span> <span data-ttu-id="04cf2-155">エンドポイントは、アドレス、バインディング、サービス コントラクトで定義します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-155">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="04cf2-156">アドレスとは、サービスが配備された場所のことです。</span><span class="sxs-lookup"><span data-stu-id="04cf2-156">The address defines where the service is located.</span></span> <span data-ttu-id="04cf2-157">バインディングはサービスとの通信方法を表します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-157">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="04cf2-158">サービス コントラクトとは、サービスが実行できる操作の定義のことです。</span><span class="sxs-lookup"><span data-stu-id="04cf2-158">The service contract defines the operations that the service can perform.</span></span>  
  
 <span data-ttu-id="04cf2-159">サービス コントラクトは通常、インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> および <xref:System.ServiceModel.OperationContractAttribute> を追加して定義します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-159">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>  
  
```  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <span data-ttu-id="04cf2-160"><xref:System.ServiceModel.ServiceContractAttribute> 、インターフェイスが、WCF サービス コントラクトを定義することを指定し、 <xref:System.ServiceModel.OperationContractAttribute> 、存在する場合、インターフェイスのメソッドを定義するサービス コントラクトの操作を示します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-160">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a WCF service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>  
  
 <span data-ttu-id="04cf2-161">このようにして定義されたサービス コントラクトをクラスとして実装します。サービス コントラクトを定義するインターフェイスを実装するクラスという形で記述します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-161">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>  
  
```  
public class Service : IEcho  
{  
    public string Echo(string input)  
    {  
       return input;  
    }  
}  
```  
  
 <span data-ttu-id="04cf2-162">WCF サービスとしての入力をサービス コントラクトを実装するクラスと呼びます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-162">A class that implements a service contract is referred to as a service type in WCF.</span></span>  
  
 <span data-ttu-id="04cf2-163">次に、アドレスとバインディングを、サービス型と関連付けます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-163">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="04cf2-164">通常、ファイルを直接編集することによって、または WCF に用意されている構成エディターを使用して構成ファイルで行われます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-164">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with WCF.</span></span> <span data-ttu-id="04cf2-165">構成ファイルの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-165">Here is an example of a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="04cf2-166">バインディングは、アプリケーションとの通信に使う一連のプロトコルを表します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-166">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="04cf2-167">一般的なシステム指定のバインディングを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-167">The following table lists the system-provided bindings that represent common options.</span></span>  
  
|<span data-ttu-id="04cf2-168">名前</span><span class="sxs-lookup"><span data-stu-id="04cf2-168">Name</span></span>|<span data-ttu-id="04cf2-169">目的</span><span class="sxs-lookup"><span data-stu-id="04cf2-169">Purpose</span></span>|  
|----------|-------------|  
|<span data-ttu-id="04cf2-170">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="04cf2-170">BasicHttpBinding</span></span>|<span data-ttu-id="04cf2-171">WS-BasicProfile 1.1 および Basic Security Profile 1.0 に対応した Web サービスやクライアントとの相互運用性。</span><span class="sxs-lookup"><span data-stu-id="04cf2-171">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|  
|<span data-ttu-id="04cf2-172">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="04cf2-172">WSHttpBinding</span></span>|<span data-ttu-id="04cf2-173">HTTP 上の WS-\* プロトコルに対応した Web サービスやクライアントとの相互運用性。</span><span class="sxs-lookup"><span data-stu-id="04cf2-173">Interoperability with Web services and clients that support the WS-\* protocols over HTTP.</span></span>|  
|<span data-ttu-id="04cf2-174">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="04cf2-174">WSDualHttpBinding</span></span>|<span data-ttu-id="04cf2-175">双方向 HTTP 通信。最初のメッセージの受信者は送信元に直接は応答せず、代わりに、WS-\* プロトコルに準拠した HTTP で、ある期間にわたって任意の数の応答を送信することができます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-175">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-\* protocols.</span></span>|  
|<span data-ttu-id="04cf2-176">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="04cf2-176">WSFederationBinding</span></span>|<span data-ttu-id="04cf2-177">HTTP 通信。サービスのリソースに対するアクセスを、明示的に指定された資格情報プロバイダーによって発行された証明書に基づいて制御することができます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-177">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|  
|<span data-ttu-id="04cf2-178">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="04cf2-178">NetTcpBinding</span></span>|<span data-ttu-id="04cf2-179">ネットワーク経由で WCF ソフトウェア エンティティ間のセキュリティで保護された、信頼性の高い、高パフォーマンス通信します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-179">Secure, reliable, high-performance communication between WCF software entities across a network.</span></span>|  
|<span data-ttu-id="04cf2-180">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="04cf2-180">NetNamedPipeBinding</span></span>|<span data-ttu-id="04cf2-181">同じコンピューター上の WCF ソフトウェア エンティティ間のセキュリティで保護された、信頼性の高い、高パフォーマンス通信します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-181">Secure, reliable, high-performance communication between WCF software entities on the same machine.</span></span>|  
|<span data-ttu-id="04cf2-182">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="04cf2-182">NetMsmqBinding</span></span>|<span data-ttu-id="04cf2-183">MSMQ を使用して WCF ソフトウェア エンティティ間の通信します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-183">Communication between WCF software entities by using MSMQ.</span></span>|  
|<span data-ttu-id="04cf2-184">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="04cf2-184">MsmqIntegrationBinding</span></span>|<span data-ttu-id="04cf2-185">WCF のソフトウェア エンティティと MSMQ を使用して別のソフトウェア エンティティ間の通信します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-185">Communication between a WCF software entity and another software entity by using MSMQ.</span></span>|  
|<span data-ttu-id="04cf2-186">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="04cf2-186">NetPeerTcpBinding</span></span>|<span data-ttu-id="04cf2-187">Windows ピア ツー ピア ネットワークを使用して WCF ソフトウェア エンティティ間の通信します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-187">Communication between WCF software entities by using Windows Peer-to-Peer Networking.</span></span>|  
  
 <span data-ttu-id="04cf2-188">システム指定のバインディングである <xref:System.ServiceModel.BasicHttpBinding> には、ASP.NET Web サービスが対応している一連のプロトコルが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="04cf2-188">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="04cf2-189">WCF アプリケーション用の独自バインディングは、WCF を使用して個々 のプロトコルを実装するバインド要素クラスのコレクションとして簡単に定義されます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-189">Custom bindings for WCF applications are easily defined as collections of the binding element classes that WCF uses to implement individual protocols.</span></span> <span data-ttu-id="04cf2-190">追加のプロトコルを表す、新しいバインド要素を記述することも可能です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-190">New binding elements can be written to represent additional protocols.</span></span>  
  
 <span data-ttu-id="04cf2-191">サービス型の内部的な動作は、動作を表すクラス群のプロパティで調整できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-191">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="04cf2-192">次の例で、<xref:System.ServiceModel.ServiceBehaviorAttribute> クラスは、サービス型がマルチスレッド処理されることを指定しています。</span><span class="sxs-lookup"><span data-stu-id="04cf2-192">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 <span data-ttu-id="04cf2-193"><xref:System.ServiceModel.ServiceBehaviorAttribute> など、属性として定義された動作もあります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-193">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="04cf2-194">これに対し、管理者がプロパティを設定できる動作は、アプリケーションの構成ファイルで変更することができます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-194">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>  
  
 <span data-ttu-id="04cf2-195">サービス型のプログラムの記述には、多くの場合 <xref:System.ServiceModel.OperationContext> クラスを使います。</span><span class="sxs-lookup"><span data-stu-id="04cf2-195">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="04cf2-196">静的プロパティである <xref:System.ServiceModel.OperationContext.Current%2A> を介して、実行コンテキストに関する情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-196">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="04cf2-197"><xref:System.ServiceModel.OperationContext> の使い方は、<xref:System.Web.HttpContext> クラスや <xref:System.EnterpriseServices.ContextUtil> クラスと同様です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-197"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="04cf2-198">ホスト</span><span class="sxs-lookup"><span data-stu-id="04cf2-198">Hosting</span></span>  
 <span data-ttu-id="04cf2-199">ASP.NET Web サービスは、コンパイルしてクラス ライブラリ アセンブリの形になっています。</span><span class="sxs-lookup"><span data-stu-id="04cf2-199">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="04cf2-200">サービス ファイルという、拡張子が .asmx のファイルの `@ WebService` ディレクティブに、サービスの実行コードが組み込まれたクラスと、これを収容するアセンブリが定義されています。</span><span class="sxs-lookup"><span data-stu-id="04cf2-200">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 <span data-ttu-id="04cf2-201">サービス ファイルをインターネット インフォメーション サービス (IIS) の ASP.NET アプリケーション ルート、アセンブリをアプリケーション ルートのサブディレクトリ \bin 以下にコピーすると、</span><span class="sxs-lookup"><span data-stu-id="04cf2-201">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="04cf2-202">このサービス ファイルの URL (Uniform Resource Locator) でアプリケーションにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-202">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>  
  
 <span data-ttu-id="04cf2-203">および任意の .NET アプリケーション内で IIS 5.1 または 6.0 では、Windows プロセス アクティブ化サービス (WAS) は IIS 7.0 の一部として提供する、WCF サービスをホスト簡単にできます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-203">WCF services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="04cf2-204">ただし IIS 5.1/6.0 の場合、通信トランスポート プロトコルは HTTP に限ります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-204">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>  
  
 <span data-ttu-id="04cf2-205">IIS 5.1/6.0 または WAS 上でサービスをホストする手順を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-205">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>  
  
1.  <span data-ttu-id="04cf2-206">サービス型をコンパイルしてクラス ライブラリ アセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-206">Compile the service type into a class library assembly.</span></span>  
  
2.  <span data-ttu-id="04cf2-207">拡張子を .svc としたサービス ファイルを作り、サービス型を `@ ServiceHost` ディレクティブで次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-207">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  <span data-ttu-id="04cf2-208">サービス ファイルを仮想ディレクトリにコピーし、アセンブリをその仮想ディレクトリの \bin サブディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="04cf2-208">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>  
  
4.  <span data-ttu-id="04cf2-209">構成ファイルを仮想ディレクトリに、Web.config という名前でコピーします。</span><span class="sxs-lookup"><span data-stu-id="04cf2-209">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>  
  
 <span data-ttu-id="04cf2-210">するとアプリケーションには、アプリケーション ルートに置いたサービス ファイルの URL でアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-210">The application is then accessible by using the URL of the service file in the application root.</span></span>  
  
 <span data-ttu-id="04cf2-211">.NET アプリケーション内で WCF サービスをホストするサービス型、アプリケーションによって参照されるクラス ライブラリ アセンブリをコンパイルし、サービスを使用して、ホストにアプリケーションをプログラミング、<xref:System.ServiceModel.ServiceHost>クラスです。</span><span class="sxs-lookup"><span data-stu-id="04cf2-211">To host a WCF service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="04cf2-212">サービスを管理する基本的なプログラムの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-212">The following is an example of the basic programming required:</span></span>  
  
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
  
 <span data-ttu-id="04cf2-213">この例では <xref:System.ServiceModel.ServiceHost> の構築時にトランスポート プロトコルに対してアドレスを指定しています。</span><span class="sxs-lookup"><span data-stu-id="04cf2-213">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="04cf2-214">このアドレスをベース アドレスと呼びます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-214">These addresses are referred to as base addresses.</span></span>  
  
 <span data-ttu-id="04cf2-215">WCF サービスのエンドポイントに指定されたアドレスは、エンドポイントのホストのベース アドレスに対する相対アドレスです。</span><span class="sxs-lookup"><span data-stu-id="04cf2-215">The address provided for any endpoint of a WCF service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="04cf2-216">ホストではトランスポート プロトコルごとに 1 つベース アドレスを設定できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-216">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="04cf2-217">上記の構成ファイルの構成例では、エンドポイントに対して選択された <xref:System.ServiceModel.BasicHttpBinding> はトランスポート プロトコルとして HTTP を使用しているので、エンドポイント `EchoService` のアドレスは、HTTP に対して設定されたベース アドレスを基準としたものになります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-217">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="04cf2-218">前の例で、ホストの場合、HTTP ベース アドレスはhttp://www.contoso.com:8000/します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-218">In the case of the host in the preceding example, the HTTP base address is http://www.contoso.com:8000/.</span></span> <span data-ttu-id="04cf2-219">なお、IIS や WAS 上でホストされているサービスの場合、ベース アドレスはサービス ファイルの URL になります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-219">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>  
  
 <span data-ttu-id="04cf2-220">WCF の ASP.NET 互換モード オプションを使用する IIS または WAS、およびが構成されている HTTP でトランスポート プロトコルとしてのみでホストされているサービスのみが可能です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-220">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use WCF ASP.NET compatibility mode option.</span></span> <span data-ttu-id="04cf2-221">ASP.NET 互換モードは、次の 2 つの手順で切り替えます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-221">Turning that option on requires the following steps.</span></span>  
  
1.  <span data-ttu-id="04cf2-222">プログラムの開発者は、サービス型に <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 属性を追加し、ASP.NET 互換モードに切り替えることができる、または切り替えることが必須である旨の指定をしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-222">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>  
  
    ```  
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(  
          RequirementsMode=AspNetCompatbilityRequirementsMode.Require)]  
    public class DerivativesCalculatorServiceType: IDerivativesCalculator  
    ```  
  
2.  <span data-ttu-id="04cf2-223">管理者は、アプリケーションが ASP.NET 互換モードで動作するよう、次のように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-223">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>  
  
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
  
     <span data-ttu-id="04cf2-224">WCF アプリケーションは、.asmx を使用する、拡張子として .svc ではなく、サービス ファイルを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-224">WCF applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>  
  
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
  
     <span data-ttu-id="04cf2-225">このオプションでは、Url を使用して、.asmx サービス ファイルのサービスを変更するときに WCF を使用して構成されているクライアントを変更する必要がなくなります保存できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-225">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use WCF.</span></span>  
  
## <a name="client-development"></a><span data-ttu-id="04cf2-226">クライアント開発</span><span class="sxs-lookup"><span data-stu-id="04cf2-226">Client Development</span></span>  
 <span data-ttu-id="04cf2-227">ASP.NET Web サービスのクライアントの開発にはコマンド ライン ツール WSDL.exe を使用します.asmx ファイルの URL を入力として指定します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-227">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="04cf2-228">WCF に用意された、対応するツールは[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-228">The corresponding tool provided by WCF is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="04cf2-229">サービス コントラクトの定義と WCF クライアント クラスの定義を持つコード モジュールを生成します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-229">It generates a code module with the definition of the service contract and the definition of a WCF client class.</span></span> <span data-ttu-id="04cf2-230">また、サービスのアドレスとバインディングを指定して、構成ファイルを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-230">It also generates a configuration file with the address and binding of the service.</span></span>  
  
 <span data-ttu-id="04cf2-231">リモート サービスのクライアントを開発する場合、通常は、非同期パターンに従ってプログラムを記述するようお勧めします。</span><span class="sxs-lookup"><span data-stu-id="04cf2-231">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="04cf2-232">WSDL.exe ツールは、特段の指定をしなくても、同期パターンと非同期パターンを使ったコードをそれぞれ生成します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-232">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="04cf2-233">によって生成されたコード、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)いずれかのパターンを提供できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-233">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="04cf2-234">特に指定しなければ同期パターン用です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-234">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="04cf2-235">`/async` スイッチを指定して実行すれば、生成されるコードは非同期パターン用になります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-235">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>  
  
 <span data-ttu-id="04cf2-236">ASP によって生成された WCF クライアント クラス内の名前を示す保証はありません。NET の WSDL.exe ツールでは、既定では、Svcutil.exe ツールによって生成された WCF クライアント クラス内の名前と一致します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-236">There is no guarantee that names in the WCF client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in WCF client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="04cf2-237">特に、<xref:System.Xml.Serialization.XmlSerializer> でシリアル化したクラスのプロパティ名は、Svcutil.exe で生成した場合 "Property" という接頭辞が付きますが、WSDL.exe の場合はそうなりません。</span><span class="sxs-lookup"><span data-stu-id="04cf2-237">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>  
  
## <a name="message-representation"></a><span data-ttu-id="04cf2-238">メッセージ表現</span><span class="sxs-lookup"><span data-stu-id="04cf2-238">Message Representation</span></span>  
 <span data-ttu-id="04cf2-239">ASP.NET Web サービスとやり取りする SOAP メッセージのヘッダーはカスタマイズ可能です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-239">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="04cf2-240"><xref:System.Web.Services.Protocols.SoapHeader> の派生クラスでヘッダーの構造を定義し、<xref:System.Web.Services.Protocols.SoapHeaderAttribute> でヘッダーが存在することを指定します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-240">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>  
  
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
  
 <span data-ttu-id="04cf2-241">WCF は、属性、 <xref:System.ServiceModel.MessageContractAttribute>、 <xref:System.ServiceModel.MessageHeaderAttribute>、および<xref:System.ServiceModel.MessageBodyMemberAttribute>サービスによって送受信される SOAP メッセージの構造を記述します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-241">The WCF provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>  
  
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
  
 <span data-ttu-id="04cf2-242">この構文でメッセージ構造を明示的に記述できますが、ASP.NET Web サービスのコードからメッセージ構造を導くことも可能です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-242">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="04cf2-243">また、ASP.NET の構文ではメッセージ ヘッダーとして表現されます、サービスのプロパティなど、`ProtocolHeader`前の例では、プロパティが WCF の構文ではメッセージのプロパティとしてより正確に表されます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-243">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in WCF syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="04cf2-244">また、WCF では、エンドポイントの構成に追加するメッセージ ヘッダーができます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-244">Also, WCF allows message headers to be added to the configuration of endpoints.</span></span>  
  
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
  
 <span data-ttu-id="04cf2-245">この方法では、クライアントやサービスのコード内で、基盤となるプロトコル ヘッダーを参照しなくても済みます。エンドポイントが適切に構成されているので、ヘッダーがメッセージ中に取り込まれるからです。</span><span class="sxs-lookup"><span data-stu-id="04cf2-245">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>  
  
## <a name="service-description"></a><span data-ttu-id="04cf2-246">サービスの説明</span><span class="sxs-lookup"><span data-stu-id="04cf2-246">Service Description</span></span>  
 <span data-ttu-id="04cf2-247">WSDL で記述したクエリを HTTP GET 要求として発行して、ASP.NET Web サービスの .asmx ファイルを取得しようとすると、ASP.NET は WSDL によるサービス記述を生成し、</span><span class="sxs-lookup"><span data-stu-id="04cf2-247">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="04cf2-248">要求に対する応答として返します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-248">It returns that WSDL as the response to the request.</span></span>  
  
 <span data-ttu-id="04cf2-249">ASP.NET 2.0 では、サービスが Web Services-Interoperability Organization (WS-I) の Basic Profile 1.1 に準拠していることを検証し、その旨を WSDL による記述に追加できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="04cf2-249">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="04cf2-250">この処理には、`ConformsTo` 属性の `EmitConformanceClaims` および <xref:System.Web.Services.WebServiceBindingAttribute> パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-250">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="04cf2-251">ASP.NET が WSDL で生成したサービス記述はカスタマイズ可能です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-251">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="04cf2-252"><xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> の派生クラスを作成し、WSDL による記述に項目を追加する、という形でカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="04cf2-252">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>  
  
 <span data-ttu-id="04cf2-253">WCF サービスを記述する wsdl 応答には、WCF サービスの .svc ファイルに対するクエリの WSDL に HTTP GET 要求を発行する、IIS 51 内でホストされている HTTP エンドポイントを持つ、6.0 または WAS からさせます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-253">Issuing an HTTP GET request with the query WSDL for the .svc file of a WCF service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes WCF to respond with WSDL to describe the service.</span></span> <span data-ttu-id="04cf2-254">httpGetEnabled が true に設定されている場合は、WSDL で記述したクエリを HTTP GET 要求として、.NET アプリケーション上でホストされているサービスの HTTP ベース アドレスに発行しても同じ効力があります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-254">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>  
  
 <span data-ttu-id="04cf2-255">ただし、WCF は、サービスの説明に生成された WSDL を使って、Ws-metadataexchange 要求にも応答します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-255">However, WCF also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="04cf2-256">ASP.NET Web サービスには、WS-MetadataExchange 要求に応答する機能がありません。</span><span class="sxs-lookup"><span data-stu-id="04cf2-256">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>  
  
 <span data-ttu-id="04cf2-257">WCF によって生成される WSDL を広範囲にカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-257">The WSDL that WCF generates can be extensively customized.</span></span> <span data-ttu-id="04cf2-258"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> クラスには、WSDL による記述をカスタマイズするための機能がいくつか組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="04cf2-258">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="04cf2-259">WCF ではなくファイルを使用して、静的な WSDL で特定の URL が、WSDL を生成しないことにも構成することができます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-259">The WCF can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>  
  
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
  
## <a name="exception-handling"></a><span data-ttu-id="04cf2-260">例外処理</span><span class="sxs-lookup"><span data-stu-id="04cf2-260">Exception Handling</span></span>  
 <span data-ttu-id="04cf2-261">ASP.NET Web サービスでは、処理できない例外が発生すると、SOAP エラーとしてクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-261">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="04cf2-262">また、<xref:System.Web.Services.Protocols.SoapException> クラスのインスタンスを明示的にスローして、クライアント側に SOAP エラーの詳しい状況を通知し、より適切に管理させることも可能です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-262">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>  
  
 <span data-ttu-id="04cf2-263">WCF サービスで未処理の例外は返されませんをクライアントに機密情報が誤って、例外を通じて公開されることを防ぐために SOAP エラーとして。</span><span class="sxs-lookup"><span data-stu-id="04cf2-263">In WCF services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="04cf2-264">ただしデバッグ目的で、このような例外をクライアントに返すように設定することは可能です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-264">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>  
  
 <span data-ttu-id="04cf2-265">SOAP エラーをクライアントに返す場合、データ コントラクト型を汎用型 <xref:System.ServiceModel.FaultException%601> のインスタンスとしてキャストし、これをスローする方法が使えます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-265">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="04cf2-266">また、操作に <xref:System.ServiceModel.FaultContractAttribute> 属性を追加して、操作で生じうるエラーを指定する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-266">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>  
  
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
  
 <span data-ttu-id="04cf2-267">これにより、サービスで発生する可能性のあるエラーが WSDL の形で公開されます。クライアント側の開発者は、当該操作によりどのようなエラーが生じうるかをあらかじめ予測し、catch ブロック内に適切な処理を組み込んでおくことができます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-267">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>  
  
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
  
## <a name="state-management"></a><span data-ttu-id="04cf2-268">状態管理</span><span class="sxs-lookup"><span data-stu-id="04cf2-268">State Management</span></span>  
 <span data-ttu-id="04cf2-269">ASP.NET Web サービスの実装には <xref:System.Web.Services.WebService> の派生クラスを使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-269">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>  
  
```  
public class Service : WebService, IEcho  
{  
  
 public string Echo(string input)  
 {  
  return input;  
 }  
}  
```  
  
 <span data-ttu-id="04cf2-270">この場合、基本クラス <xref:System.Web.Services.WebService> に定義された Context プロパティを使って、<xref:System.Web.HttpContext> オブジェクトにアクセスすることになります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-270">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="04cf2-271"><xref:System.Web.HttpContext> オブジェクトには、アプリケーションやセッションの状態情報をそれぞれ更新、取得する、Application プロパティ、Session プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-271">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>  
  
 <span data-ttu-id="04cf2-272">ASP.NET では、<xref:System.Web.HttpContext> の Session プロパティでアクセスするセッション状態情報の、実際の格納場所を細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-272">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="04cf2-273">格納場所としては、クッキー内、データベース内、稼動中のサーバーのメモリ上、状態管理用の特別なサーバーのメモリ上があり、</span><span class="sxs-lookup"><span data-stu-id="04cf2-273">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="04cf2-274">サービスの構成ファイルで指定します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-274">The choice is made in the service’s configuration file.</span></span>  
  
 <span data-ttu-id="04cf2-275">WCF では、状態管理の拡張可能なオブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-275">The WCF provides extensible objects for state management.</span></span> <span data-ttu-id="04cf2-276">いずれも <xref:System.ServiceModel.IExtensibleObject%601> を実装しています。</span><span class="sxs-lookup"><span data-stu-id="04cf2-276">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="04cf2-277">中でも重要な拡張可能オブジェクトは、<xref:System.ServiceModel.ServiceHostBase> および <xref:System.ServiceModel.InstanceContext> です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-277">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="04cf2-278">`ServiceHostBase` を使用すると、同一ホスト上の全サービス型のあらゆるインスタンスからアクセスできる状態を管理できます。一方、`InstanceContext` を使用すると、同じサービス型のインスタンス内で実行されるコードからアクセスできる状態を管理できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-278">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>  
  
 <span data-ttu-id="04cf2-279">ここでは、サービスの種類、`TradingSystem`が、<xref:System.ServiceModel.ServiceBehaviorAttribute>同じ WCF クライアント インスタンスからのすべての呼び出しが、サービス型の同じインスタンスにルーティングされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-279">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same WCF client instance are routed to the same instance of the service type.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class TradingSystem: ITradingService  
```  
  
 <span data-ttu-id="04cf2-280">次のクラス `DealData` に定義されている状態には、同じサービス型のインスタンス内で実行されるどのコードからでもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-280">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>  
  
```  
internal class DealData: IExtension<InstanceContext>  
{  
 public string DealIdentifier = null;  
 public Trade[] Trades = null;  
}  
```  
  
 <span data-ttu-id="04cf2-281">サービス コントラクトの操作のいずれかを実装するサービス型のコードでは、状態オブジェクト `DealData` を、当該サービス型の現在のインスタンスに関する状態として追加することができます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-281">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>  
  
```  
string ITradingService.BeginDeal()  
{  
 string dealIdentifier = Guid.NewGuid().ToString();  
 DealData state = new DealData(dealIdentifier);  
 OperationContext.Current.InstanceContext.Extensions.Add(state);  
 return dealIdentifier;  
}  
```  
  
 <span data-ttu-id="04cf2-282">この状態オブジェクトは、サービス コントラクトの他の操作を実装するコードから取得、更新できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-282">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>  
  
```  
void ITradingService.AddTrade(Trade trade)  
{  
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();  
 dealData.AddTrade(trade);  
}  
```  
  
 <span data-ttu-id="04cf2-283">状態の情報が、ASP.NET 経由でコントロールを提供する一方、<xref:System.Web.HttpContext>クラスが格納されている実際には、WCF には、少なくとも、初期のバージョンでは拡張可能なオブジェクトの格納場所を制御します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-283">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, WCF, at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="04cf2-284">WCF サービスの ASP.NET 互換モードを選択する最適な理由を構成するとします。</span><span class="sxs-lookup"><span data-stu-id="04cf2-284">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a WCF service.</span></span> <span data-ttu-id="04cf2-285">このような制御が不可欠な応用の場合、ASP.NET 互換モードにすれば、ASP.NET と同様に <xref:System.Web.HttpContext> クラスの機能を活用できるばかりでなく、<xref:System.Web.HttpContext> クラスで管理する状態情報の実際の格納場所も制御できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-285">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>  
  
## <a name="security"></a><span data-ttu-id="04cf2-286">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="04cf2-286">Security</span></span>  
 <span data-ttu-id="04cf2-287">ASP.NET Web サービスのセキュリティ保全の手順は、IIS アプリケーションのセキュリティ保全の手順と同じです。</span><span class="sxs-lookup"><span data-stu-id="04cf2-287">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="04cf2-288">WCF アプリケーションは、IIS 内だけでなく、その .NET 実行可能ファイル内でも、ホストされていることができます、ための WCF アプリケーションをセキュリティで保護するためのオプションに IIS の機能から独立して行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-288">Because WCF applications can be hosted not only within IIS but also within any .NET executable, the options for securing WCF applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="04cf2-289">ただし、ASP.NET Web サービスを提供する機能も ASP.NET 互換モードで実行されている WCF サービスで利用できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-289">However, the facilities provided for ASP.NET Web services are also available for WCF services running in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-authentication"></a><span data-ttu-id="04cf2-290">セキュリティ : 認証</span><span class="sxs-lookup"><span data-stu-id="04cf2-290">Security: Authentication</span></span>  
 <span data-ttu-id="04cf2-291">IIS にはアプリケーションへのアクセス制御機能が組み込まれており、匿名アクセスの他、Windows 認証、ダイジェスト認証、基本認証、.NET パスポート認証など、さまざまな認証モードを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-291">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="04cf2-292">Windows 認証は、ASP.NET Web サービスへのアクセス制御に使えます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-292">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="04cf2-293">ただし、WCF アプリケーションは、IIS でホストされる、ときに、その認証は、さまざまな他のオプションの Windows 認証をサポートして、WCF によって管理できるように、アプリケーションへの匿名アクセスを許可するように IIS を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-293">However, when WCF applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by WCF itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="04cf2-294">他の認証方法としては、ユーザー名トークン、X.509 証明書、SAML トークン、CardSpace カードなどが組み込まれていますが、独自の認証機構を定義することも可能です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-294">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>  
  
### <a name="security-impersonation"></a><span data-ttu-id="04cf2-295">セキュリティ : 偽装</span><span class="sxs-lookup"><span data-stu-id="04cf2-295">Security: Impersonation</span></span>  
 <span data-ttu-id="04cf2-296">ASP.NET Web サービスは ASP.NET の ID 要素を使用して、あるユーザーに偽装することができます。あらかじめ設定した特定のユーザーでなくても、要求に資格情報が添えられていれば、その要求元ユーザーに偽装できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-296">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="04cf2-297">その要素は、ASP.NET 互換モードで実行される WCF アプリケーションの権限借用の構成を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-297">That element can be used to configure impersonation in WCF applications running in ASP.NET compatibility mode.</span></span>  
  
 <span data-ttu-id="04cf2-298">WCF 構成システムは、特定の権限を借用するユーザーを指定するため、独自の id 要素を提供します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-298">The WCF configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="04cf2-299">また、WCF クライアントとサービス別に構成できます権限借用のためです。</span><span class="sxs-lookup"><span data-stu-id="04cf2-299">Also, WCF clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="04cf2-300">クライアント側では、要求を送信する現在のユーザーに偽装する構成が可能です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-300">Clients can be configured to impersonate the current user when they transmit requests.</span></span>  
  
```xml  
<behaviors>  
     <behavior name="DerivativesCalculatorClientBehavior">  
      <clientCredentials>  
      <windows allowedImpersonationLevel="Impersonation"/>  
      </clientCredentials>  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="04cf2-301">サービス側では、現在の要求と共に提供された資格情報のユーザーに偽装するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-301">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public void Receive(Message input)  
```  
  
### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="04cf2-302">セキュリティ : アクセス制御リストによる承認</span><span class="sxs-lookup"><span data-stu-id="04cf2-302">Security: Authorization using Access Control Lists</span></span>  
 <span data-ttu-id="04cf2-303">アクセス制御リスト (ACL) を使って .asmx ファイルへのアクセスを制限できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-303">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="04cf2-304">ただし、WCF .svc ファイルの Acl は、ASP.NET 互換モードでを除き無視されます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-304">However, ACLs on WCF .svc files are ignored except in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-role-based-authorization"></a><span data-ttu-id="04cf2-305">セキュリティ : ロール ベースの承認</span><span class="sxs-lookup"><span data-stu-id="04cf2-305">Security: Role-based Authorization</span></span>  
 <span data-ttu-id="04cf2-306">IIS の Windows 認証オプションを、ASP.NET 構成言語の承認要素と組み合わせて使用すると、ASP.NET Web サービスに対し、各ユーザーが属する Windows グループに基づくロール ベースの承認機構を提供できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-306">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="04cf2-307">ASP.NET 2.0 には、より汎用的なロール ベースの承認機構である、ロール プロバイダーが導入されました。</span><span class="sxs-lookup"><span data-stu-id="04cf2-307">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>  
  
 <span data-ttu-id="04cf2-308">ロール プロバイダーとは、ユーザーが割り当てられたロールに関する問い合わせを行う、基本インターフェイスを実装したクラス群です。各ロール プロバイダーには、さまざまな情報源から必要な情報を取得する手段が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="04cf2-308">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="04cf2-309">ASP.NET 2.0 には、Microsoft SQL Server データベースからロールの割り当てを検索できるロール プロバイダーと、Windows Server 2003 承認マネージャーから検索できるロール プロバイダーがあります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-309">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>  
  
 <span data-ttu-id="04cf2-310">ロール プロバイダーの機構は、WCF アプリケーションを含む、任意の .NET アプリケーションで ASP.NET とは無関係に実際に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-310">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a WCF application.</span></span> <span data-ttu-id="04cf2-311">WCF アプリケーションの次のサンプルの構成方法を示します ASP.NET ロール プロバイダーを使用して選択したオプション、<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-311">The following sample configuration for a WCF application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
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
  
### <a name="security-claims-based-authorization"></a><span data-ttu-id="04cf2-312">セキュリティ : クレーム ベースの承認</span><span class="sxs-lookup"><span data-stu-id="04cf2-312">Security: Claims-based Authorization</span></span>  
 <span data-ttu-id="04cf2-313">WCF の最も重要な技術革新の 1 つは、クレーム ベースの保護されたリソースへのアクセスを承認するための完全なサポートです。</span><span class="sxs-lookup"><span data-stu-id="04cf2-313">One of the most important innovations of WCF is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="04cf2-314">クレームは、型、権限、および値で構成されます。たとえば、運転免許証を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="04cf2-314">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="04cf2-315">ここには所持者に関する誕生日などの情報 (ここでいう「クレーム」) が記載されています。</span><span class="sxs-lookup"><span data-stu-id="04cf2-315">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="04cf2-316">つまり、クレームの型は「誕生日」、値は運転者の実際の誕生日です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-316">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="04cf2-317">また、クレームの権限は、所持者がこの値に対してできることを表します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-317">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="04cf2-318">誕生日について言えば、所持者はこの情報を「見る」ことはできますが、「書き換える」ことはできません。</span><span class="sxs-lookup"><span data-stu-id="04cf2-318">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="04cf2-319">クレーム ベースの承認は、ロール ベースの承認を包含する概念です。というのも、ロールはクレームの 1 つの型であると考えることができるからです。</span><span class="sxs-lookup"><span data-stu-id="04cf2-319">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>  
  
 <span data-ttu-id="04cf2-320">クレーム ベースの承認では、一連のクレームを操作のアクセス要求と比較し、その結果に応じてアクセスを許可または拒否します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-320">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="04cf2-321">WCF を使用して値を割り当てることによって信頼性情報ベースの承認をもう一度実行するクラスを指定することができます、`ServiceAuthorizationManager`プロパティ<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>です。</span><span class="sxs-lookup"><span data-stu-id="04cf2-321">In WCF, you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="04cf2-322">クレーム ベースの承認を行うクラスは、<xref:System.ServiceModel.ServiceAuthorizationManager> を継承し、`AccessCheck()` メソッドだけをオーバーライドして定義します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-322">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> <span data-ttu-id="04cf2-323">WCF がサービスの操作が呼び出され、提供されるたびに、そのメソッドを呼び出す、<xref:System.ServiceModel.OperationContext>ユーザーの要求を持つオブジェクトでその`ServiceSecurityContext.AuthorizationContext`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="04cf2-323">WCF calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> <span data-ttu-id="04cf2-324">WCF はセキュリティ トークンからユーザーに関するクレームをアセンブルし、認証のままにするは、ユーザー、それらの要求が問題の操作に十分であるかどうかを評価します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-324">WCF does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>  
  
 <span data-ttu-id="04cf2-325">WCF は、セキュリティの任意の種類からの要求を自動的にアセンブル トークンは非常に重要な技術革新の場合、コードを完全に独立して、認証メカニズムのクレーム ベースの承認を可能になったためです。</span><span class="sxs-lookup"><span data-stu-id="04cf2-325">That WCF automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="04cf2-326">これに対し、ACL やロール ベースの承認は、Windows 認証と密に関連し合っています。</span><span class="sxs-lookup"><span data-stu-id="04cf2-326">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>  
  
### <a name="security-confidentiality"></a><span data-ttu-id="04cf2-327">セキュリティ : 機密性</span><span class="sxs-lookup"><span data-stu-id="04cf2-327">Security: Confidentiality</span></span>  
 <span data-ttu-id="04cf2-328">ASP.NET Web サービスとの間でやり取りするメッセージの機密性は、トランスポート層で、IIS 上のアプリケーションが Secure Hypertext Transfer Protocol (HTTPS) を使うように構成することによって確保します。</span><span class="sxs-lookup"><span data-stu-id="04cf2-328">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="04cf2-329">同じ IIS でホストされる WCF アプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-329">The same can be done for WCF applications hosted within IIS.</span></span> <span data-ttu-id="04cf2-330">ただし、IIS の外部でホストされている WCF アプリケーションは、セキュリティで保護されたトランスポート プロトコルを使用しても構成できます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-330">However, WCF applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="04cf2-331">重要な WCF アプリケーションを構成して、Ws-security プロトコルを使用して、配送される前に、メッセージをセキュリティで保護することもできます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-331">More important, WCF applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="04cf2-332">メッセージの本体を WS-Security で保護することにより、最終送信先に到達するまでの中継ノードで機密が洩れないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-332">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>  
  
## <a name="globalization"></a><span data-ttu-id="04cf2-333">グローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="04cf2-333">Globalization</span></span>  
 <span data-ttu-id="04cf2-334">ASP.NET 構成言語では、個々のサービスごとにカルチャを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="04cf2-334">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="04cf2-335">WCF では、ASP.NET 互換モードで以外には、その構成設定はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="04cf2-335">The WCF does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="04cf2-336">ASP.NET 互換モードを使用しない WCF サービスをローカライズするには、カルチャに固有のアセンブリにサービスの種類をコンパイルして、各カルチャに固有のアセンブリのカルチャに固有の別個のエンドポイントがあります。</span><span class="sxs-lookup"><span data-stu-id="04cf2-336">To localize a WCF service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04cf2-337">関連項目</span><span class="sxs-lookup"><span data-stu-id="04cf2-337">See Also</span></span>  
 [<span data-ttu-id="04cf2-338">使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較</span><span class="sxs-lookup"><span data-stu-id="04cf2-338">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
