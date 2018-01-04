---
title: "相互運用可能なオブジェクト参照"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d74c54d29f7da085d9d87bf37cc93078726f308
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="interoperable-object-references"></a><span data-ttu-id="a79b6-102">相互運用可能なオブジェクト参照</span><span class="sxs-lookup"><span data-stu-id="a79b6-102">Interoperable Object References</span></span>
<span data-ttu-id="a79b6-103">既定では、<xref:System.Runtime.Serialization.DataContractSerializer> はオブジェクトを値でシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="a79b6-103">By default the <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="a79b6-104"><xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> プロパティを使用すると、型のオブジェクトをシリアル化する場合に、オブジェクト参照を保持するようにデータ コントラクト シリアライザーに指示できます。</span><span class="sxs-lookup"><span data-stu-id="a79b6-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the Data Contract Serializer to preserve object references when serializing objects of the type.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="a79b6-105">生成される XML</span><span class="sxs-lookup"><span data-stu-id="a79b6-105">Generated XML</span></span>  
 <span data-ttu-id="a79b6-106">例として、次のオブジェクトを考えます。</span><span class="sxs-lookup"><span data-stu-id="a79b6-106">As an example, consider the following object:</span></span>  
  
```  
[DataContract]  
public class X  
{  
    SomeClass someInstance = new SomeClass();  
    [DataMember]  
    public SomeClass A = someInstance;  
    [DataMember]  
    public SomeClass B = someInstance;  
}  
  
public class SomeClass   
{  
}  
```  
  
 <span data-ttu-id="a79b6-107"><xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> を `false` (既定値) に設定すると、次の XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a79b6-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="a79b6-108"><xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> を `true` に設定すると、次の XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a79b6-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1" />  
</X>  
```  
  
 <span data-ttu-id="a79b6-109">ただし、<xref:System.Runtime.Serialization.XsdDataContractExporter> プロパティが `id` に設定されている場合でも、`ref` がそのスキーマに `preserveObjectReferences` 属性や `true` 属性を記述することはありません。</span><span class="sxs-lookup"><span data-stu-id="a79b6-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> does not describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="a79b6-110">IsReference の使用</span><span class="sxs-lookup"><span data-stu-id="a79b6-110">Using IsReference</span></span>  
 <span data-ttu-id="a79b6-111">スキーマの記述に従った有効なオブジェクト参照情報を生成するには、<xref:System.Runtime.Serialization.DataContractAttribute> 属性を型に適用し、<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> フラグを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="a79b6-111">To generate object reference information that is valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="a79b6-112">前のサンプル クラス `IsReference` で `X` を使用するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="a79b6-112">Using `IsReference` in the previous example class `X`:</span></span>  
  
 `[DataContract(IsReference=true)] public class X`  
  
 `{`  
  
 `SomeClass someInstance = new SomeClass();`  
  
 `[DataMember]`  
  
 `public SomeClass A = someInstance;`  
  
 `[DataMember]`  
  
 `public SomeClass B = someInstance;`  
  
 `}`  
  
 `public class SomeClass`  
  
 `{`  
  
 `}`  
  
 <span data-ttu-id="a79b6-113">次のような XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a79b6-113">The generated XML is as follows:</span></span>  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 <span data-ttu-id="a79b6-114">`IsReference` を使用すると、メッセージのラウンド トリップに対応できます。</span><span class="sxs-lookup"><span data-stu-id="a79b6-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="a79b6-115">これを使用しない場合、型をスキーマから生成しても、その型に対して返された XML に、もともと想定していたスキーマとの互換性があるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="a79b6-115">Without it, when a type is generated from schema, what is sent back as XML for that type is not necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="a79b6-116">つまり、`id` 属性と `ref` 属性がシリアル化されたとしても、元のスキーマによってこれらの属性 (またはすべての属性) が拒否される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a79b6-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="a79b6-117">`IsReference` をデータ メンバーに適用すれば、そのメンバーは、ラウンド トリップ時にも "参照可能" として認識され続けます。</span><span class="sxs-lookup"><span data-stu-id="a79b6-117">With `IsReference` applied to a data member, the member continues to be recognized as "referenceable" when roundtripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a79b6-118">参照</span><span class="sxs-lookup"><span data-stu-id="a79b6-118">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
