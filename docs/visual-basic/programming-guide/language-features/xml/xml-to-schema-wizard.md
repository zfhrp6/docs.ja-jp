---
title: "XML to Schema Wizard (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlToSchemaWizard"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML IntelliSense [Visual Basic]"
  - "XML [Visual Basic], IntelliSense"
  - "IntelliSense [Visual Basic], XML"
  - "XML schemas, creating"
ms.assetid: 98c495ba-8f37-4517-a0db-aa738611ab76
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# XML to Schema Wizard (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

XML to Schema ウィザードを使用すると、1 つ以上の XML ドキュメントから推論される XML スキーマ セットを作成し、プロジェクトに追加できます。  テキスト ファイル形式の XML ドキュメント、HTTP インターネット アドレスからの XML、および XML to Schema ウィザードに入力するか貼り付ける XML を任意に組み合わせて使用できます。  
  
 XML スキーマは、Visual Basic で XML プロパティ用の IntelliSense を提供するのに使用されます。  詳細については、「[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)」および「[XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)」を参照してください。  
  
> [!NOTE]
>  XML to Schema ウィザードを実行する前に、このウィザードによって前回生成されたすべての既存の XSD ファイルをプロジェクトから削除しておくことをお勧めします。  推論したスキーマ セットが既存の XML スキーマ セットと一致すると、競合が発生して、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] が XML プロパティ用の IntelliSense を提供できなくなります。  
  
 XML to Schema ウィザードは、<xref:System.Xml.Schema.XmlSchemaInference> クラスを使用して指定の XML のスキーマを作成します。  その結果、目的のスキーマ セット用に複数のスキーマ ファイルが作成される場合があります。  指定の XML 内の XML 名前空間ごとに 1 つの拡張スキーマ定義 \(XSD\) ファイルが作成されます。  詳細については、<xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドのトピックを参照してください。  
  
 XML to Schema ウィザードにアクセスするには、**\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックし、**\[データ\]** と **\[共通項目\]** のいずれかのテンプレート グループから **XML to Schema** テンプレートを追加します。  XML スキーマ セットを推論する対象の XML ドキュメント ソースをすべて追加したら、**\[OK\]** をクリックして推論されるスキーマ セットを作成します。  
  
 **\[ソースの種類\]**  
 この列には、XML ドキュメント ソースの種類として、**\[ファイル\]**、**\[URL\]**、または **\[XML\]** が表示されます。  
  
 **\[XML ドキュメントの場所\]**  
 この列には、XML ドキュメントのパスが表示されます。  入力した XML ドキュメントまたは貼り付けた XML ドキュメントについては、XML ドキュメントの内容が表示されます。  
  
 **\[ファイルから追加\]**  
 ファイル エクスプローラーを使用して XML ドキュメント ファイルを追加するには、このボタンをクリックします。  
  
 **\[Web から追加\]**  
 XML ドキュメントの HTTP アドレスを指定するには、このボタンをクリックします。  
  
 **\[XML の入力または貼り付け\]**  
 XML ドキュメントをダイアログ ボックスに入力するか貼り付けるには、このボタンをクリックします。  
  
## 参照  
 <xref:System.Xml.Schema.XmlSchemaInference>   
 [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)