---
title: "XML to Schema ウィザード (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlToSchemaWizard
dev_langs:
- VB
helpviewer_keywords:
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
- XML schemas, creating
ms.assetid: 98c495ba-8f37-4517-a0db-aa738611ab76
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d0c9c0247f3d9934ef973c7322cb098f9b445a5a
ms.lasthandoff: 03/13/2017

---
# <a name="xml-to-schema-wizard-visual-basic"></a>XML to Schema ウィザード (Visual Basic)
XML to Schema ウィザードを使用して、1 つまたは複数の XML ドキュメントから推論される XML スキーマ セットを作成し、プロジェクトが含まれます。 HTTP インターネット アドレスからの XML または型指定された、または XML to Schema ウィザードに貼り付ける XML テキスト ファイルの形式で XML ドキュメントの任意の組み合わせを使用することができます。  
  
 XML スキーマを使用すると、IntelliSense Visual Basic での XML プロパティを提供します。 詳細については、次を参照してください。 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)と[Visual Basic における XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)します。  
  
> [!NOTE]
>  XML to Schema ウィザードを実行する前に、以前にウィザードによって生成されたプロジェクトから既存の XSD ファイルを削除することをお勧めします。 競合が発生することができますが、既存のスキーマ セットに対応する XML スキーマ セットを推論する場合と[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]IntelliSense XML プロパティを提供することはできません。  
  
 XML to Schema ウィザードを使用して、<xref:System.Xml.Schema.XmlSchemaInference>指定された xml スキーマを作成するクラス</xref:System.Xml.Schema.XmlSchemaInference>。 その結果、スキーマ セットの複数のスキーマ ファイルが作成されます。 各 XML 名前空間の指定された XML では、拡張可能なスキーマ定義 (XSD) ファイルが作成されます。 詳細については、次を参照してください、<xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A>メソッド。</xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> 。  
  
 XML to Schema ウィザードにアクセスする をクリックして**新しい項目の追加**上、**プロジェクト**メニューを追加し、 **XML スキーマを**いずれかのテンプレート、**データ**または**の一般的な項目**テンプレート グループです。 XML スキーマ セットを推論するすべての XML ドキュメントのソースを追加したら、以下の をクリックして**OK**推論されるスキーマを作成するに設定します。  
  
 **ソースの種類**  
 この列に XML ドキュメントのソースの種類が表示されます:**ファイル**、 **URL**、または**XML**します。  
  
 **XML ドキュメントの場所**  
 この列には、XML ドキュメントのパスが表示されます。 型指定された、または貼り付けたの XML ドキュメントの XML ドキュメントの内容を表示します。  
  
 **ファイルを追加します。**  
 ファイル エクスプ ローラーを使用して XML ドキュメント ファイルを追加するには、このボタンをクリックします。  
  
 **Web から追加します。**  
 XML ドキュメントの HTTP アドレスを指定するには、このボタンをクリックします。  
  
 **入力するか、XML を貼り付けます**  
 入力するか、ダイアログ ボックスに、XML ドキュメントを貼り付けるには、このボタンをクリックします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Schema.XmlSchemaInference></xref:System.Xml.Schema.XmlSchemaInference>   
 [Visual Basic における XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)
