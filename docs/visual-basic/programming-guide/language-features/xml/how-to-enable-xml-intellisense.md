---
title: "How to: Enable XML IntelliSense in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML IntelliSense [Visual Basic]"
  - "XML [Visual Basic], IntelliSense"
  - "IntelliSense [Visual Basic], XML"
ms.assetid: af67d0ee-a4a6-4abf-9c07-5a8cfe80d111
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# How to: Enable XML IntelliSense in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic の XML IntelliSense は、XML スキーマで定義されている要素の単語入力を補完します。  Visual Basic で XML IntelliSense を有効にするには、以下を行う必要があります。  
  
1.  アプリケーションが読み書きする XML ファイルの XML スキーマ \(XSD\) ファイルを入手します。  
  
2.  XML スキーマ ファイルをプロジェクトに含めます。  
  
3.  対象の名前空間をコード ファイルまたはプロジェクトにインポートします。  対象の名前空間は、XSD スキーマの `targetNamespace` 属性または `tns` 属性によって識別されます。  
  
     対象の名前空間をインポートするには、`Imports` ステートメントを使用するか、またはプロジェクト デザイナーの **\[参照\]** ページを使用して、プロジェクトのすべてのコード ファイルに名前空間を追加します。  
  
 Visual Basic での XML IntelliSense の機能の詳細については、「[XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)」を参照してください。  XML 名前空間のインポートの詳細については、「[Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)」または「[\[参照設定\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)」を参照してください。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
 ![ビデオへのリンク](../../../../csharp/programming-guide/concepts/linq/media/playvideo.png "PlayVideo") このトピックのビデオ版については、「[Video How to: Enable XML IntelliSense in Visual Basic \(ビデオ デモ: Visual Basic で XML IntelliSense を有効にする\)](http://go.microsoft.com/fwlink/?LinkId=102466)」を参照してください。  関連のビデオ デモについては、「[How Do I Enable XML IntelliSense and Use XML Namespaces? \(XML IntelliSense を有効にして XML 名前空間を使用する方法\)](http://go.microsoft.com/fwlink/?LinkId=143035)」を参照してください。  
  
## Visual Basic で XML IntelliSense を有効にする  
 XML ファイルがあり、それに対応する XSD スキーマ ファイルがない場合、SP1 では、XML to Schema ウィザードを使用して XSD スキーマ ファイルを作成できます。  Visual Studio XML エディターでスキーマの推論を使用することもできます。  
  
#### XML to Schema ウィザードを使用して XML ファイルの XSD スキーマ ファイルを作成するには \(SP1 が必要\)  
  
1.  プロジェクトで、**\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
2.  **\[データ\]** と **\[共通項目\]** のいずれかのテンプレート カテゴリから **Xml to Schema** 項目テンプレートを選択します。  
  
3.  推論されるスキーマ セットを格納する 1 つまたは複数の XSD ファイルの名前を指定し、**\[追加\]** をクリックします。  
  
4.  **\[XML ドキュメントからの XML スキーマ セットの生成\]** ウィンドウで、XML スキーマ セットを推論する対象の 1 つ以上の XML ドキュメントを追加します。  
  
    -   ファイル エクスプローラーを使用して XML ドキュメントを含むテキスト ファイルを追加するには、をクリック **\[ファイルから追加\]**。  
  
    -   HTTP アドレスから XML ドキュメントを追加するには、**\[Web から追加\]** をクリックします。  
  
    -   XML ドキュメントの内容をウィザードにコピーまたは入力するには、**\[XML の入力または貼り付け\]** をクリックします。  
  
5.  XML スキーマ セットを推論する対象の XML ドキュメント ソースをすべて指定したら、**\[OK\]** をクリックして XML スキーマ セットを推論します。  プロジェクト フォルダーの 1 つ以上の XSD ファイルにスキーマ セットが保存されます   \(スキーマ内の XML 名前空間ごとに 1 つのファイルが作成されます\)。  
  
#### Visual Studio XML エディターでスキーマの推論を使用して XML ファイルの XSD スキーマ ファイルを作成するには  
  
1.  Visual Studio の XML デザイナーで XML ファイルを編集します。  
  
2.  カーソルが XML ファイル内のどこかにあると、**\[XML\]** メニューが表示されます。  **\[XML\]** メニューの **\[スキーマの作成\]** をクリックします。  XML ファイルから推論される XSD スキーマから、XSD ファイルが作成されます。  
  
3.  XSD スキーマ ファイルを保存します。  
  
    > [!NOTE]
    >  同一のスキーマを使用する予定の複数の XML ドキュメントから、異なる XSD スキーマが推論される場合があります。  このようなことは、特定の要素と属性がいずれかの XML だけに存在したり、含まれている要素の順序が異なっていたりする場合に、発生する可能性があります。  XSD スキーマの推論を使用するときは、推論された XSD スキーマが完全で正確であることを確認する必要があります。  
  
#### XSD スキーマ ファイルを含めるには  
  
-   既定では、Visual Basic プロジェクトには XSD ファイルは表示されません。  XSD ファイルがプロジェクトのフォルダーに既に含まれる場合は、**ソリューション エクスプローラー**で **\[すべてのファイルを表示\]** ボタンをクリックします。  **ソリューション エクスプローラー**で XSD ファイルを探し、ファイルを右クリックし、**\[プロジェクトに含める\]** をクリックします。  
  
-   XSD ファイルがまだプロジェクトの一部ではない場合は、**ソリューション エクスプローラー**で、XSD ファイルを格納するフォルダーを右クリックし、**\[追加\]** をポイントして、**\[既存の項目\]** をクリックします。  XSD ファイルを探し、**\[追加\]** をクリックします。  
  
#### コード ファイルに XML 名前空間をインポートするには  
  
1.  XSD スキーマで対象の名前空間を識別します。  
  
2.  次の例で示すように、コード ファイルの先頭に、対象の XML 名前空間の `Imports` ステートメントを追加します。  
  
     [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-enable-xml-intell_1.vb)]  
  
     既定の名前空間、つまり名前空間プレフィックスのない XML 要素および属性に適用される名前空間として、XML 名前空間をインポートするには、対象となる既定の XML 名前空間に `Imports` ステートメントを追加します。  名前空間プレフィックスは指定しないでください。  次に、`Imports` ステートメントの例を示します。  
  
     [!code-vb[VbXmlSamples#50](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/how-to-enable-xml-intell_2.vb)]  
  
#### プロジェクト内のすべてのファイルに XML 名前空間をインポートするには  
  
1.  コード ファイルにインポートされた XML 名前空間は、そのコード ファイルのみに適用されます。  プロジェクト内のすべてのコード ファイルに適用する XML 名前空間をインポートするには、**ソリューション エクスプローラー**で **\[My Project\]** をダブルクリックして、プロジェクト デザイナーを開きます。  
  
2.  **\[参照\]** タブの **\[インポートされた名前空間\]** ボックスに、完全な XML 名前空間宣言の形式 \(たとえば、`<xmlns: ns="http://sampleNamespace">`\) で、対象の XML 名前空間を入力します。  対象の XML 名前空間で名前空間プレフィックスが指定されていない場合、その名前空間はプロジェクトの既定の XML 名前空間になります。  
  
3.  **\[ユーザー インポートの追加\]** をクリックします。  
  
## 参照  
 [Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [\[参照設定\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)   
 [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)