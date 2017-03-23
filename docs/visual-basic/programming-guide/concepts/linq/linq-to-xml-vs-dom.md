---
title: "LINQ to XML およびDOM (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 18c36130-d598-40b7-9007-828232252978
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 88b6bddcdeec2859844f5d5f94777146d488b5fb
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-vs-dom-visual-basic"></a>LINQ to XML およびDOM (Visual Basic)
このセクションでは、主な違いを説明[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]と、現在主流の XML プログラミング API、W3C ドキュメント オブジェクト モデル (DOM) とします。  
  
## <a name="new-ways-to-construct-xml-trees"></a>XML ツリーを構築するための新しい方法  
 W3C DOM では、XML ツリーをボトムアップ方式で作成します。つまり、ドキュメントを作成し、要素を作成して、要素をドキュメントに追加することによって作成します。  
  
 たとえば、次になります: <xref:System.Xml.XmlDocument>:</xref:System.Xml.XmlDocument> 、DOM の Microsoft 実装を使用して XML ツリーを作成する一般的な方法  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
Dim phone1 As XmlElement = doc.CreateElement("Phone")  
phone1.SetAttribute("Type", "Home")  
phone1.InnerText = "206-555-0144"  
Dim phone2 As XmlElement = doc.CreateElement("Phone")  
phone2.SetAttribute("Type", "Work")  
phone2.InnerText = "425-555-0145"  
Dim street1 As XmlElement = doc.CreateElement("Street1")  
street1.InnerText = "123 Main St"  
Dim city As XmlElement = doc.CreateElement("City")  
city.InnerText = "Mercer Island"  
Dim state As XmlElement = doc.CreateElement("State")  
state.InnerText = "WA"  
Dim postal As XmlElement = doc.CreateElement("Postal")  
postal.InnerText = "68042"  
Dim address As XmlElement = doc.CreateElement("Address")  
address.AppendChild(street1)  
address.AppendChild(city)  
address.AppendChild(state)  
address.AppendChild(postal)  
Dim contact As XmlElement = doc.CreateElement("Contact")  
contact.AppendChild(name)  
contact.AppendChild(phone1)  
contact.AppendChild(phone2)  
contact.AppendChild(address)  
Dim contacts As XmlElement = doc.CreateElement("Contacts")  
contacts.AppendChild(contact)  
doc.AppendChild(contacts)  
Console.WriteLine(doc.OuterXml)  
```  
  
 このコーディング スタイルでは、XML ツリーの構造の多くを視覚的に認識できません。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]XML ツリーを構築するには、このアプローチをサポートしていますが、別の方法でをもサポート*関数型構築*します。 Visual basic では、関数型構築は、XML ツリーを構築するのに XML リテラルを使用します。  
  
 使用して、同じ XML ツリーを構築する方法を次に示します[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]関数型構築します。  
  
```vb  
Dim contacts = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="Home">206-555-0144</Phone>  
            <Phone Type="Work">425-555-0145</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 このように、XML ツリーを構築するコードのインデントにより、基になる XML の構造が示されます。  
  
 詳細については、次を参照してください。 [XML ツリーを作成する」(Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)します。  
  
## <a name="working-directly-with-xml-elements"></a>XML 要素の直接操作  
 一般に、XML によるプログラミングで重視されるのは XML 要素であり、その属性が重要となる場合が多くあります。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] では、XML 要素と XML 属性を直接操作できます。 たとえば、次のようなことが可能です。  
  
-   ドキュメント オブジェクトを一切使用せずに XML 要素を作成する。 これにより、XML ツリーのフラグメントを操作する際のプログラミングが単純化されます。  
  
-   `T:System.Xml.Linq.XElement` オブジェクトを直接 XML ファイルから読み込む。  
  
-   `T:System.Xml.Linq.XElement` オブジェクトをファイルやストリームにシリアル化する。  
  
 これに対して、XML ドキュメントが XML ツリーの論理的コンテナーとして使用される W3C DOM では、 XML ノード (要素や属性を含む) は XML ドキュメントのコンテキストで作成する必要があります。 DOM で name 要素を作成するコード フラグメントを以下に示します。  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 要素を複数のドキュメントで使用する場合は、ノードをドキュメント間でインポートする必要があります。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]このレイヤーの複雑さを回避できます。  
  
 使用する LINQ to XML を使用する場合、<xref:System.Xml.Linq.XDocument>クラスのドキュメントのルート レベルにコメントや処理命令を追加する場合のみです</xref:System.Xml.Linq.XDocument>。  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>名前と名前空間の処理の単純化  
 一般に XML プログラミングでは、名前、名前空間、および名前空間プレフィックスの処理が複雑になります。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]名前空間プレフィックスを処理する必要がなくなるため、名前と名前空間を簡単になります。 必要に応じて名前空間プレフィックスを制御することはできますが、 名前空間プレフィックスを明示的に制御する場合、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]が必要な場合は、かではシリアル化されていない場合は、既定の名前空間を使用する場合、シリアル化中に名前空間プレフィックスを割り当てられます。 既定の名前空間が使用された場合は、結果のドキュメントには名前空間プレフィックスは含まれません。 詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。  
  
 DOM にはその他に、ノードの名前を変更できないという問題もあります。 ノード名の変更が必要な場合は、新しいノードを作成し、そこにすべての子ノードをコピーする必要があります。この場合、元のノード固有の特性は失われます。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]設定できるようにすることによってこの問題を回避、 <xref:System.Xml.Linq.XName>、ノードのプロパティ</xref:System.Xml.Linq.XName>。  
  
## <a name="static-method-support-for-loading-xml"></a>XML を読み込むための静的メソッドのサポート  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]インスタンス メソッドの代わりに、静的メソッドを使用して、XML を読み込むことができます。 これにより、読み込みと解析が簡略化されます。 詳細については、次を参照してください。[方法: ロード XML ファイル (Visual Basic の場合) から](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)します。  
  
## <a name="removal-of-support-for-dtd-constructs"></a>DTD の構成要素に関するサポートの削除  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] では、XML プログラミングのさらなる簡略化のために、エンティティとエンティティ参照のサポートが削除されています。 エンティティの管理は複雑で、ほとんど利用されていません。 これらのサポートを削除することにより、パフォーマンスが向上し、プログラミング インターフェイスが簡略化されます。 ときに、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]ツリーが設定されると、すべての DTD エンティティが展開します。  
  
## <a name="support-for-fragments"></a>フラグメントのサポート  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]対応する要素の管轄外の`XmlDocumentFragment`クラスです。 ただし、多くの場合、`XmlDocumentFragment`概念として型指定されたクエリの結果によって処理できる<xref:System.Collections.Generic.IEnumerable%601>の<xref:System.Xml.Linq.XNode>、または<xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement></xref:System.Collections.Generic.IEnumerable%601></xref:System.Xml.Linq.XNode></xref:System.Collections.Generic.IEnumerable%601>。  
  
## <a name="support-for-xpathnavigator"></a>XPathNavigator のサポート  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]サポートを提供<xref:System.Xml.XPath.XPathNavigator>拡張メソッドによって、<xref:System.Xml.XPath?displayProperty=fullName>名前空間</xref:System.Xml.XPath?displayProperty=fullName></xref:System.Xml.XPath.XPathNavigator>。 詳細については、 <xref:System.Xml.XPath.Extensions?displayProperty=fullName>。</xref:System.Xml.XPath.Extensions?displayProperty=fullName>を参照してください。  
  
## <a name="support-for-white-space-and-indentation"></a>空白とインデントのサポート  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]空白をもっと簡単に処理 DOM より  
  
 一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。 書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。 これが [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の既定の動作です。  
  
 もう&1; つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。 場合によっては、このインデントを一切変更しないようにする必要があります。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] でこれを実現するには、XML を読み込む際または解析する際に空白を維持し、XML をシリアル化するときに書式設定を無効にします。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]として空白文字を格納、<xref:System.Xml.Linq.XText>ノード、特殊な<xref:System.Xml.XmlNodeType>は dom ノード型</xref:System.Xml.XmlNodeType></xref:System.Xml.Linq.XText>。  
  
## <a name="support-for-annotations"></a>注釈のサポート  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 要素は、注釈の拡張可能なセットをサポートしています。 このサポートは、スキーマの情報、要素が UI にバインドされているかどうかの情報、またはアプリケーション固有のその他の情報など、要素に関するさまざまな情報を追跡する場合に利用できます。 詳細については、次を参照してください。 [LINQ to XML の注釈](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5)します。  
  
## <a name="support-for-schema-information"></a>スキーマ情報のサポート  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]拡張メソッドによって XSD 検証のサポートを提供、<xref:System.Xml.Schema?displayProperty=fullName>名前空間</xref:System.Xml.Schema?displayProperty=fullName>。 これにより、XML ツリーが XSD に準拠しているかどうかを検証できます。 また、スキーマ検証後の情報セット (PSVI) を使用して XML ツリーを設定できます。 詳細については、次を参照してください[方法: 検証を使用して XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) <xref:System.Xml.Schema.Extensions>.</xref:System.Xml.Schema.Extensions> 。  
  
## <a name="see-also"></a>関連項目  
 [はじめに (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
