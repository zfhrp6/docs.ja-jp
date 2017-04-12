---
title: "XDocument クラスの概要 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 31111b23adb019aad3ad55787c073dc02446291d
ms.lasthandoff: 03/13/2017

---
# <a name="xdocument-class-overview-visual-basic"></a>XDocument クラスの概要 (Visual Basic)
このトピックに<xref:System.Xml.Linq.XDocument>クラス</xref:System.Xml.Linq.XDocument>が導入されています  
  
## <a name="overview-of-the-xdocument-class"></a>XDocument クラスの概要  
 <xref:System.Xml.Linq.XDocument>クラスには、有効な XML ドキュメントに必要な情報が含まれています</xref:System.Xml.Linq.XDocument>。 これには、XML 宣言、処理命令、コメントが含まれます。  
  
 <xref:System.Xml.Linq.XDocument><xref:System.Xml.Linq.XDocument>クラス</xref:System.Xml.Linq.XDocument>によって提供される特定の機能を必要とする場合のオブジェクト</xref:System.Xml.Linq.XDocument>を作成する必要がだけに注意してください。 多くの状況では、 <xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>を直接操作できます。 直接操作<xref:System.Xml.Linq.XElement>は比較的単純なプログラミング モデル</xref:System.Xml.Linq.XElement>。  
  
 <xref:System.Xml.Linq.XDocument><xref:System.Xml.Linq.XContainer>。</xref:System.Xml.Linq.XContainer>から派生します。</xref:System.Xml.Linq.XDocument> したがって子ノードを含めることができます。 ただし、<xref:System.Xml.Linq.XDocument>オブジェクトが&1; つだけの子を持つ<xref:System.Xml.Linq.XElement>ノード</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument>。 これは、XML ドキュメントにルート要素を&1; つしか持てないという XML 標準を反映しています。  
  
## <a name="components-of-xdocument"></a>XDocument のコンポーネント  
 <xref:System.Xml.Linq.XDocument>、次の要素を含めることができます:</xref:System.Xml.Linq.XDocument>  
  
-   1 つ<xref:System.Xml.Linq.XDeclaration>オブジェクト</xref:System.Xml.Linq.XDeclaration>。 <xref:System.Xml.Linq.XDeclaration>XML 宣言の関連部分を指定することができます。 XML バージョン、ドキュメントのエンコードおよび XML ドキュメントがスタンドアロンかどうか。</xref:System.Xml.Linq.XDeclaration>  
  
-   1 つ<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。 これは XML ドキュメントのルート ノードです。  
  
-   任意の数の<xref:System.Xml.Linq.XProcessingInstruction>オブジェクト</xref:System.Xml.Linq.XProcessingInstruction>。 処理命令は、XML を処理するアプリケーションに情報を伝達します。  
  
-   任意の数の<xref:System.Xml.Linq.XComment>オブジェクト</xref:System.Xml.Linq.XComment>。 コメントは、ルート要素の兄弟になります。 <xref:System.Xml.Linq.XComment>オブジェクトは、XML ドキュメントのコメントで始めることはできませんので、一覧の最初の引数にすることはできません</xref:System.Xml.Linq.XComment>。  
  
-   1 つ<xref:System.Xml.Linq.XDocumentType>DTD 用</xref:System.Xml.Linq.XDocumentType>。  
  
 シリアル化すると、<xref:System.Xml.Linq.XDocument>場合でも、`XDocument.Declaration`は`null`、ライターがある場合、出力は XML 宣言には`Writer.Settings.OmitXmlDeclaration`に設定`false`(既定値).</xref:System.Xml.Linq.XDocument>  
  
 既定では、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] によってバージョンが "1.0" に、エンコードが "utf-8" に設定されます。  
  
## <a name="using-xelement-without-xdocument"></a>XDocument なしでの XElement の使用  
 既に触れましたが、<xref:System.Xml.Linq.XElement>クラスが主なクラスで、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]プログラミング インターフェイスです</xref:System.Xml.Linq.XElement>。 多くの場合、アプリケーションはドキュメントの作成を必要としません。 使用して、<xref:System.Xml.Linq.XElement>クラス、XML ツリーを作成、他の XML ツリーを追加して、XML ツリーを変更および保存すればすべて</xref:System.Xml.Linq.XElement>  
  
## <a name="using-xdocument"></a>XDocument の使用  
 構築する、 <xref:System.Xml.Linq.XDocument>、構築する場合と同じように、関数型構築を使用して<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument>。  
  
 次のコード作成、<xref:System.Xml.Linq.XDocument>オブジェクトおよびそれに関連する格納されるオブジェクト</xref:System.Xml.Linq.XDocument>。  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
                       <!--This is a comment.-->  
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
                       <Pubs>  
                           <Book>  
                               <Title>Artifacts of Roman Civilization</Title>  
                               <Author>Moreno, Jordao</Author>  
                           </Book>  
                           <Book>  
                               <Title>Midieval Tools and Implements</Title>  
                               <Author>Gazit, Inbar</Author>  
                           </Book>  
                       </Pubs>  
                       <!--This is another comment.-->  
doc.Save("test.xml")  
```  
  
 ファイル test.xml を調べると、次の出力が生成されます。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML プログラミングの概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
