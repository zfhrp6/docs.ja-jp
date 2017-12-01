---
title: "XML ドキュメントの作成"
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
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a0806e34cfbf7c8e0b5ba995ca4876b8d10405e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-creation"></a>XML ドキュメントの作成
XML ドキュメントは、2 とおりの方法で作成できます。 作成する方法の 1 つは、 **XmlDocument**パラメーターなしでします。 その他の方法は、作成する、 **XmlDocument**を XmlNameTable をパラメーターとして渡します。 次の例は、新しい、空を作成する方法を示しています。 **XmlDocument**パラメーターを使用します。  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 ドキュメントを作成した後は、文字列からのデータを読み込むことができますストリーム、URL、テキスト リーダー、または**XmlReader**派生したクラスを使用して、**読み込む**メソッドです。 別のロード メソッドも、 **LoadXML**メソッドで、文字列から XML を読み取ります。 詳細については、さまざまな**ロード**メソッドを参照してください[DOM に XML ドキュメントを読み取る](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)です。  
  
 呼ばれるクラスがある、 **XmlNameTable**です。 このクラスは、分解された文字列オブジェクトのテーブルです。 このテーブルを使用すると、パーサーは XML ドキュメント内で繰り返されているすべての要素名と属性名に同じ文字列オブジェクトを使用でき、効率が向上します。 **XmlNameTable**ドキュメントが上記のように作成され、ドキュメントが読み込まれるときに、属性と要素の名前に読み込まれるときに自動的に作成します。 使用して新しいドキュメントを作成するには、ネーム テーブルを持つドキュメントが既にある場合、それらの名前が別のドキュメントで役に立つ、**ロード**を受け取るメソッド、 **XmlNameTable**をパラメーターとして。 既存の機能を使用してこのメソッドを使用して、ドキュメントが作成されると、 **XmlNameTable**のすべての属性と既に読み込まれます。 その他のドキュメントから要素。 XmlNameTable を使用すると、要素名と属性名を効率的に比較できます。 詳細については、 **XmlNameTable**を参照してください[比較 XmlNameTable によるオブジェクトの](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)します。 リファレンスについては、次を参照してください。<xref:System.Xml.XmlNameTable>です。  
  
## <a name="see-also"></a>関連項目  
 [XML ドキュメント オブジェクト モデル (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
