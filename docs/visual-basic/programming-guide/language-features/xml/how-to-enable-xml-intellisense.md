---
title: "方法: Visual Basic における XML IntelliSense を有効にする |Microsoft ドキュメント"
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
helpviewer_keywords:
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
ms.assetid: af67d0ee-a4a6-4abf-9c07-5a8cfe80d111
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 84af19189fa3fc510c8d4f8e408cbb2a393d8b8f
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-enable-xml-intellisense-in-visual-basic"></a>方法 : Visual Basic で XML IntelliSense を有効にする
Visual Basic における XML IntelliSense では、XML スキーマで定義されている要素の単語の入力候補を提供します。 Visual Basic における XML IntelliSense を有効にするには、次の操作を行う必要があります。  
  
1.  XML スキーマ (XSD) ファイルまたはアプリケーションはからの読み取りや書き込みを XML ファイルのファイルを取得します。  
  
2.  XML スキーマ ファイルをプロジェクトに含めます。  
  
3.  コード ファイルまたはプロジェクトには、ターゲットの名前空間または名前空間をインポートします。 ターゲットの名前空間がで識別される、`targetNamespace`または`tns`XSD スキーマの属性です。  
  
     ターゲットの名前空間をインポートするには、使用、`Imports`ステートメントを使用して、プロジェクト内のすべてのコード ファイルの名前空間を追加または、**参照**プロジェクト デザイナーのページです。  
  
 Visual Basic における XML IntelliSense の機能の詳細については、次を参照してください。 [Visual Basic における XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)します。 XML 名前空間をインポートする方法の詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)または[参照設定 ページ、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
 ![ビデオへのリンク](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo")このトピックのビデオ版について、次を参照してください。[ビデオ デモ: Visual Basic における XML IntelliSense を有効にする](http://go.microsoft.com/fwlink/?LinkId=102466)です。 関連するビデオ デモについては、次を参照してください。 [XML IntelliSense を有効にすると使用する XML 名前空間 How Do I?](http://go.microsoft.com/fwlink/?LinkId=143035)します。  
  
## <a name="enable-xml-intellisense-in-visual-basic"></a>Visual Basic における XML IntelliSense を有効にします。  
 XML ファイルがある用に XSD スキーマ ファイルがない場合、SP1 ですることができます XSD スキーマ ファイルを使用して作成 XML to Schema ウィザード。 また、Visual Studio XML エディターで、スキーマの推論を使用することもことができます。  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-the-xml-to-schema-wizard-requires-sp1"></a>XML to Schema ウィザードを使用して XML ファイルの XSD スキーマ ファイルを作成するには、(SP1 が必要)  
  
1.  プロジェクトで、次のようにクリックします。**新しい項目の追加**上、**プロジェクト**メニュー。  
  
2.  選択、 **Xml スキーマを**いずれかの項目テンプレート、**データ**または**の一般的な項目**テンプレート カテゴリ。  
  
3.  XSD ファイルまたは推論されたスキーマ セットに格納されますし、ファイルのファイル名を指定**追加**します。  
  
4.  **XML ドキュメントから XML スキーマの推論が設定**ウィンドウで、セットから XML スキーマを推論する&1; つまたは複数の XML ドキュメントを追加します。  
  
    -   ファイル エクスプ ローラーを使用して XML ドキュメントを含むテキスト ファイルを追加するに**ファイルから追加**します。  
  
    -   HTTP アドレスからの XML ドキュメントを追加するには、クリックして**Web から追加**します。  
  
    -   コピーするか、ウィザードに、XML ドキュメントの内容を入力、クリックして**の入力または貼り付け XML**します。  
  
5.  XML スキーマ セットを推論 をクリックするすべての XML ドキュメントのソースを指定した**ok** XML スキーマの推論に設定します。 スキーマ セットは、1 つ以上の XSD ファイルで、プロジェクト フォルダーに保存されます。 (各 XML 名前空間のスキーマ内のファイルが作成されます。)  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-schema-inference-in-the-visual-studio-xml-editor"></a>Visual Studio XML エディターでスキーマの推論を使用して、XML ファイルの XSD スキーマ ファイルを作成するには  
  
1.  Visual Studio XML デザイナーでの XML ファイルを編集します。  
  
2.  XML ファイルにカーソルがどこかにあるときに、 **XML**メニューが表示されます。 をクリックして**Create Schema**上、 **XML**メニュー。 XSD ファイルは、XML ファイルから推論された XSD スキーマから作成されます。  
  
3.  XSD スキーマ ファイルを保存します。  
  
    > [!NOTE]
    >  別の XSD スキーマは、同じスキーマを使用するためのものでは複数の XML ドキュメントから推論することがあります。 これは、1 つの XML ファイルでは、特定の要素と属性が見つかったときに、または要素が次に例を異なる順序で含まれる場合に発生することができます。 XSD スキーマの推論を使用する場合は、間違いがないため推論された XSD スキーマを確認してください。  
  
#### <a name="to-include-an-xsd-schema-file"></a>XSD スキーマ ファイルを追加するには  
  
-   既定では、Visual Basic プロジェクトで XSD ファイルを参照してくださいことはできません。 XSD ファイルがプロジェクトのフォルダーに既に含まれている場合はクリックして、 **すべてのファイル**ボタン**ソリューション エクスプ ローラー**します。 XSD ファイルを探し**ソリューション エクスプ ローラー**、ファイルを右クリックし、クリックして、**プロジェクトにインクルード ファイル**します。  
  
-   かどうかは、XSD ファイルされていない場合、プロジェクトの一部**ソリューション エクスプ ローラー**をポイントし、XSD ファイルを格納するフォルダーを右クリックして**追加**、クリックして**既存項目の**です。 XSD ファイルを見つけて、クリックして**追加**します。  
  
#### <a name="to-import-an-xml-namespace-in-a-code-file"></a>コード ファイルで XML 名前空間をインポートするには  
  
1.  XSD スキーマからターゲットの名前空間を識別します。  
  
2.  コード ファイルの先頭に追加、`Imports`ターゲット XML 名前空間は、次の例で示すようにステートメントです。  
  
     [!code-vb[VbXMLSamples&#1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_1.vb)]  
  
     既定の名前空間と XML 名前空間をインポートするには、XML 要素と名前空間プレフィックスがない属性に適用されている名前空間を追加、`Imports`ターゲット既定の XML 名前空間のステートメントです。 名前空間プレフィックスを指定しません。 次の例に示します、`Imports`ステートメントです。  
  
     [!code-vb[VbXmlSamples #&50;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_2.vb)]  
  
#### <a name="to-import-an-xml-namespace-for-all-files-in-a-project"></a>プロジェクト内のすべてのファイルの XML 名前空間をインポートするには  
  
1.  コード ファイルにインポートされた XML 名前空間は、そのコード ファイルのみに適用されます。 プロジェクト内のすべてのコード ファイルに適用される XML 名前空間をインポートするには、ダブルクリックすると、プロジェクト デザイナーを開き**My Project**で**ソリューション エクスプ ローラー**します。  
  
2.  **参照**] タブの [、**インポートされた名前空間**ボックスに、完全な XML 名前空間宣言の形式でターゲットの XML 名前空間を入力 (たとえば、 `<xmlns: ns="http://sampleNamespace">`)。 ターゲットの XML 名前空間が名前空間プレフィックスを指定しない場合、名前空間は、プロジェクトの既定の XML 名前空間になります。  
  
3.  クリックして**ユーザー インポートの追加**します。  
  
## <a name="see-also"></a>関連項目  
 [Imports ステートメント (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)   
 [Visual Basic における XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)

