---
title: "XmlNameTable によるオブジェクトの比較"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0cd1a3bad69499b4804299adecabad3a43b5eab1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="object-comparison-using-xmlnametable"></a>XmlNameTable によるオブジェクトの比較
**XmlDocuments**を作成すると、そのドキュメント用に作成された名前のテーブルがあります。 属性と要素の名前が入れられます、ドキュメントに XML が読み込まれるか、新しい要素や属性を作成、ときに、 **XmlNameTable**です。 作成することも、 **XmlDocument**既存**NameTable**別のドキュメントからです。 ときに**XmlDocuments**を受け取るコンス トラクターで作成された、 **XmlNameTable**パラメーター、ドキュメントがノード名、名前空間、およびに既に格納されているプレフィックスへのアクセス、 **XmlNameTable**です。 どのような方法で名前テーブルと名前が読み込まれたとしても、いったんテーブルに名前が格納されると、文字列比較によってではなく、オブジェクト比較を利用して高速に名前を比較できます。 名前のテーブルを使用する文字列を追加することも、<xref:System.Xml.NameTable.Add%2A>です。 次のコード サンプルは、名前のテーブルを作成し、文字列を示します**MyString**テーブルに追加されています。 その後、 **XmlDocument**そのテーブル、および内の要素と属性名を使用して作成された**Myfile.xml**既存の名前テーブルに追加されます。  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 ドキュメントを作成し、ドキュメントに 2 つの新しい要素を追加し、それらの要素をドキュメントの名前テーブルにも追加して、名前のオブジェクト比較を実行するコード サンプルを次に示します。  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 上記のように 2 つのドキュメント間で名前テーブルが渡される状況は、同じタイプのドキュメントを繰り返し処理する場合によく発生します。たとえば、XML スキーマ定義言語 (XSD) スキーマまたはドキュメント型定義 (DTD) に準拠し、同じ文字列が繰り返し使われる発注ドキュメントを e コマース サイトで処理する場合などです。 このような場合は、同じ要素名が複数のドキュメントに現れるため、同じ名前テーブルを使用することによってパフォーマンスが向上します。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
