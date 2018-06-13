---
title: '方法 : XML ストリームの代替要素名を指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, overriding
- serialization, overriding
- XML stream, specifying alternate element name for
- overriding XML serialization
- classes, overriding
- overriding classes
ms.assetid: 5cc1c0b0-f94b-4525-9a41-88a582cd6668
ms.openlocfilehash: d0e48c9c28c8d9447b22fa5ea7a8024442e09295
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587711"
---
# <a name="how-to-specify-an-alternate-element-name-for-an-xml-stream"></a><span data-ttu-id="dfec4-102">方法 : XML ストリームの代替要素名を指定する</span><span class="sxs-lookup"><span data-stu-id="dfec4-102">How to: Specify an Alternate Element Name for an XML Stream</span></span>
[<span data-ttu-id="dfec4-103">コード例</span><span class="sxs-lookup"><span data-stu-id="dfec4-103">Code Example</span></span>](#cpconoverridingserializationofclasseswithxmlattributeoverridesclassanchor1)  
  
 <span data-ttu-id="dfec4-104">[XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx) を使用して、クラスのセットが同じ XML ストリームを複数生成できます。</span><span class="sxs-lookup"><span data-stu-id="dfec4-104">Using the [XmlSerializer](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx), you can generate more than one XML stream with the same set of classes.</span></span> <span data-ttu-id="dfec4-105">このような作業が必要になるのは、2 つの異なる XML Web サービスが、若干の違いのある同じ基本情報を要求するような場合です。</span><span class="sxs-lookup"><span data-stu-id="dfec4-105">You might want to do this because two different XML Web services require the same basic information, with only slight differences.</span></span> <span data-ttu-id="dfec4-106">たとえば、書籍の注文を処理する 2 つの XML Web サービスがあり、どちらにも ISBN 番号が必要であるとします。</span><span class="sxs-lookup"><span data-stu-id="dfec4-106">For example, imagine two XML Web services that process orders for books, and thus both require ISBN numbers.</span></span> <span data-ttu-id="dfec4-107">一方のサービスは \<ISBN> タグを使用しますが、もう一方は \<BookID> タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="dfec4-107">One service uses the tag \<ISBN> while the second uses the tag \<BookID>.</span></span> <span data-ttu-id="dfec4-108">`Book` という名前のフィールドを含む、`ISBN` という名前のクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="dfec4-108">You have a class named `Book` that contains a field named `ISBN`.</span></span> <span data-ttu-id="dfec4-109">`Book` クラスのインスタンスがシリアル化されると、既定では、メンバー名 (ISBN) がタグ要素名として使用されます。</span><span class="sxs-lookup"><span data-stu-id="dfec4-109">When an instance of the `Book` class is serialized, it will, by default, use the member name (ISBN) as the tag element name.</span></span> <span data-ttu-id="dfec4-110">最初の XML Web サービスの場合、この既定どおりで問題ありません。</span><span class="sxs-lookup"><span data-stu-id="dfec4-110">For the first XML Web service, this is as expected.</span></span> <span data-ttu-id="dfec4-111">一方、2 つ目の XML Web サービスに XML ストリームを送信するには、タグの要素名が `BookID` になるようにシリアル化をオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dfec4-111">But to send the XML stream to the second XML Web service, you must override the serialization so that the tag's element name is `BookID`.</span></span>  
  
### <a name="to-create-an-xml-stream-with-an-alternate-element-name"></a><span data-ttu-id="dfec4-112">代替要素名で XML ストリームを作成するには</span><span class="sxs-lookup"><span data-stu-id="dfec4-112">To create an XML stream with an alternate element name</span></span>  
  
1.  <span data-ttu-id="dfec4-113"><xref:System.Xml.Serialization.XmlElementAttribute> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dfec4-113">Create an instance of the <xref:System.Xml.Serialization.XmlElementAttribute> class.</span></span>  
  
2.  <span data-ttu-id="dfec4-114"><xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> の <xref:System.Xml.Serialization.XmlElementAttribute> を "BookID" に設定します。</span><span class="sxs-lookup"><span data-stu-id="dfec4-114">Set the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> of the <xref:System.Xml.Serialization.XmlElementAttribute> to "BookID".</span></span>  
  
3.  <span data-ttu-id="dfec4-115"><xref:System.Xml.Serialization.XmlAttributes> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dfec4-115">Create an instance of the <xref:System.Xml.Serialization.XmlAttributes> class.</span></span>  
  
4.  <span data-ttu-id="dfec4-116">`XmlElementAttribute` オブジェクトを <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> の <xref:System.Xml.Serialization.XmlAttributes> プロパティによってアクセスされるコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="dfec4-116">Add the `XmlElementAttribute` object to the collection accessed through the <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> property of <xref:System.Xml.Serialization.XmlAttributes> .</span></span>  
  
5.  <span data-ttu-id="dfec4-117"><xref:System.Xml.Serialization.XmlAttributeOverrides> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dfec4-117">Create an instance of the <xref:System.Xml.Serialization.XmlAttributeOverrides> class.</span></span>  
  
6.  <span data-ttu-id="dfec4-118">`XmlAttributes` を <xref:System.Xml.Serialization.XmlAttributeOverrides> に追加し、オーバーライドするオブジェクトの型とオーバーライドされるメンバーの名前を渡します。</span><span class="sxs-lookup"><span data-stu-id="dfec4-118">Add the `XmlAttributes` to the <xref:System.Xml.Serialization.XmlAttributeOverrides>, passing the type of the object to override and the name of the member being overridden.</span></span>  
  
7.  <span data-ttu-id="dfec4-119">`XmlSerializer` を使用して、`XmlAttributeOverrides` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dfec4-119">Create an instance of the `XmlSerializer` class with `XmlAttributeOverrides`.</span></span>  
  
8.  <span data-ttu-id="dfec4-120">`Book` クラスのインスタンスを作成し、シリアル化または逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="dfec4-120">Create an instance of the `Book` class, and serialize or deserialize it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfec4-121">例</span><span class="sxs-lookup"><span data-stu-id="dfec4-121">Example</span></span>  
  
```vb  
Public Class SerializeOverride()  
    ' Creates an XmlElementAttribute with the alternate name.  
    Dim myElementAttribute As XmlElementAttribute = _  
    New XmlElementAttribute()  
    myElementAttribute.ElementName = "BookID"  
    Dim myAttributes As XmlAttributes = New XmlAttributes()  
    myAttributes.XmlElements.Add(myElementAttribute)  
    Dim myOverrides As XmlAttributeOverrides = New XmlAttributeOverrides()  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes)  
    Dim mySerializer As XmlSerializer = _  
    New XmlSerializer(GetType(Book), myOverrides)  
    Dim b As Book = New Book()  
    b.ISBN = "123456789"  
    ' Creates a StreamWriter to write the XML stream to.  
    Dim writer As StreamWriter = New StreamWriter("Book.xml")  
    mySerializer.Serialize(writer, b);  
End Class  
```  
  
```csharp  
public class SerializeOverride()  
{  
    // Creates an XmlElementAttribute with the alternate name.  
    XmlElementAttribute myElementAttribute = new XmlElementAttribute();  
    myElementAttribute.ElementName = "BookID";  
    XmlAttributes myAttributes = new XmlAttributes();  
    myAttributes.XmlElements.Add(myElementAttribute);  
    XmlAttributeOverrides myOverrides = new XmlAttributeOverrides();  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes);  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(Book), myOverrides)  
    Book b = new Book();  
    b.ISBN = "123456789"  
    // Creates a StreamWriter to write the XML stream to.  
    StreamWriter writer = new StreamWriter("Book.xml");  
    mySerializer.Serialize(writer, b);  
}  
```  
  
 <span data-ttu-id="dfec4-122">XML ストリームは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="dfec4-122">The XML stream might resemble the following.</span></span>  
  
```xml  
<Book>  
    <BookID>123456789</BookID>  
</Book>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dfec4-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="dfec4-123">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlElementAttribute>  
 <xref:System.Xml.Serialization.XmlAttributes>  
 <xref:System.Xml.Serialization.XmlAttributeOverrides>  
 [<span data-ttu-id="dfec4-124">XML シリアル化および SOAP シリアル化</span><span class="sxs-lookup"><span data-stu-id="dfec4-124">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [<span data-ttu-id="dfec4-125">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="dfec4-125">XmlSerializer</span></span>](https://msdn.microsoft.com/library/system.xml.serialization.xmlserializer.aspx)  
 [<span data-ttu-id="dfec4-126">方法 : オブジェクトをシリアル化する</span><span class="sxs-lookup"><span data-stu-id="dfec4-126">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="dfec4-127">方法 : オブジェクトを逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="dfec4-127">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 [<span data-ttu-id="dfec4-128">方法 : オブジェクトを逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="dfec4-128">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
