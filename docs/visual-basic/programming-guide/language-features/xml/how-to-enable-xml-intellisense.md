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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: e367016c93586ad34492628b6a4384a5ef1b6acd
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-enable-xml-intellisense-in-visual-basic"></a><span data-ttu-id="58679-102">方法 : Visual Basic で XML IntelliSense を有効にする</span><span class="sxs-lookup"><span data-stu-id="58679-102">How to: Enable XML IntelliSense in Visual Basic</span></span>
<span data-ttu-id="58679-103">Visual Basic における XML IntelliSense では、XML スキーマで定義されている要素の単語の入力候補を提供します。</span><span class="sxs-lookup"><span data-stu-id="58679-103">XML IntelliSense in Visual Basic provides word completion for elements that are defined in an XML schema.</span></span> <span data-ttu-id="58679-104">Visual Basic における XML IntelliSense を有効にするには、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="58679-104">To enable XML IntelliSense in Visual Basic, you must do the following:</span></span>  
  
1.  <span data-ttu-id="58679-105">XML スキーマ (XSD) ファイルまたはアプリケーションはからの読み取りや書き込みを XML ファイルのファイルを取得します。</span><span class="sxs-lookup"><span data-stu-id="58679-105">Obtain the XML schema (XSD) file or files for the XML files that your application will read from or write to.</span></span>  
  
2.  <span data-ttu-id="58679-106">XML スキーマ ファイルをプロジェクトに含めます。</span><span class="sxs-lookup"><span data-stu-id="58679-106">Include the XML schema files in your project.</span></span>  
  
3.  <span data-ttu-id="58679-107">コード ファイルまたはプロジェクトには、ターゲットの名前空間または名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="58679-107">Import the target namespace or namespaces into your code file or project.</span></span> <span data-ttu-id="58679-108">ターゲットの名前空間がで識別される、`targetNamespace`または`tns`XSD スキーマの属性です。</span><span class="sxs-lookup"><span data-stu-id="58679-108">A target namespace is identified by the `targetNamespace` or `tns` attribute of your XSD schema.</span></span>  
  
     <span data-ttu-id="58679-109">ターゲットの名前空間をインポートするには、使用、`Imports`ステートメントを使用して、プロジェクト内のすべてのコード ファイルの名前空間を追加または、**参照**プロジェクト デザイナーのページです。</span><span class="sxs-lookup"><span data-stu-id="58679-109">To import a target namespace, use the `Imports` statement, or add a namespace for all code files in a project by using the **References** page of the Project Designer.</span></span>  
  
 <span data-ttu-id="58679-110">Visual Basic における XML IntelliSense の機能の詳細については、次を参照してください。 [Visual Basic における XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)します。</span><span class="sxs-lookup"><span data-stu-id="58679-110">For more information on the capabilities of XML IntelliSense in Visual Basic, see [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md).</span></span> <span data-ttu-id="58679-111">XML 名前空間をインポートする方法の詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)または[参照設定 ページ、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="58679-111">For more information on importing XML namespaces, see [Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) or [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="58679-112">![ビデオへのリンク](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo")このトピックのビデオ版について、次を参照してください。[ビデオ デモ: Visual Basic における XML IntelliSense を有効にする](http://go.microsoft.com/fwlink/?LinkId=102466)です。</span><span class="sxs-lookup"><span data-stu-id="58679-112">![link to video](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") For a video version of this topic, see [Video How to: Enable XML IntelliSense in Visual Basic](http://go.microsoft.com/fwlink/?LinkId=102466).</span></span> <span data-ttu-id="58679-113">関連するビデオ デモについては、次を参照してください。 [XML IntelliSense を有効にすると使用する XML 名前空間 How Do I?](http://go.microsoft.com/fwlink/?LinkId=143035)します。</span><span class="sxs-lookup"><span data-stu-id="58679-113">For a related video demonstration, see [How Do I Enable XML IntelliSense and Use XML Namespaces?](http://go.microsoft.com/fwlink/?LinkId=143035).</span></span>  
  
## <a name="enable-xml-intellisense-in-visual-basic"></a><span data-ttu-id="58679-114">Visual Basic における XML IntelliSense を有効にします。</span><span class="sxs-lookup"><span data-stu-id="58679-114">Enable XML IntelliSense in Visual Basic</span></span>  
 <span data-ttu-id="58679-115">XML ファイルがある用に XSD スキーマ ファイルがない場合、SP1 ですることができます XSD スキーマ ファイルを使用して作成 XML to Schema ウィザード。</span><span class="sxs-lookup"><span data-stu-id="58679-115">If you have an XML file but you do not have an XSD schema file for it, in SP1 you can create an XSD schema file by using the XML to Schema Wizard.</span></span> <span data-ttu-id="58679-116">また、Visual Studio XML エディターで、スキーマの推論を使用することもことができます。</span><span class="sxs-lookup"><span data-stu-id="58679-116">You can also use schema inference in the Visual Studio XML Editor.</span></span>  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-the-xml-to-schema-wizard-requires-sp1"></a><span data-ttu-id="58679-117">XML to Schema ウィザードを使用して XML ファイルの XSD スキーマ ファイルを作成するには、(SP1 が必要)</span><span class="sxs-lookup"><span data-stu-id="58679-117">To create an XSD schema file for an XML file by using the XML to Schema Wizard (requires SP1)</span></span>  
  
1.  <span data-ttu-id="58679-118">プロジェクトで、次のようにクリックします。**新しい項目の追加**上、**プロジェクト**メニュー。</span><span class="sxs-lookup"><span data-stu-id="58679-118">In your project, click **Add New Item** on the **Project** menu.</span></span>  
  
2.  <span data-ttu-id="58679-119">選択、 **Xml スキーマを**いずれかの項目テンプレート、**データ**または**の一般的な項目**テンプレート カテゴリ。</span><span class="sxs-lookup"><span data-stu-id="58679-119">Select the **Xml to Schema** item template from either the **Data** or **Common Items** template categories.</span></span>  
  
3.  <span data-ttu-id="58679-120">XSD ファイルまたは推論されたスキーマ セットに格納されますし、ファイルのファイル名を指定**追加**します。</span><span class="sxs-lookup"><span data-stu-id="58679-120">Provide a file name for the XSD file or files that the inferred schema set will be stored in, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="58679-121">**XML ドキュメントから XML スキーマの推論が設定**ウィンドウで、セットから XML スキーマを推論する&1; つまたは複数の XML ドキュメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="58679-121">In the **Infer XML Schema set from XML documents** window, add one or more XML documents to infer the XML schema set from.</span></span>  
  
    -   <span data-ttu-id="58679-122">ファイル エクスプ ローラーを使用して XML ドキュメントを含むテキスト ファイルを追加するに**ファイルから追加**します。</span><span class="sxs-lookup"><span data-stu-id="58679-122">To add text files that contain XML documents by using File Explorer, click **Add from File**.</span></span>  
  
    -   <span data-ttu-id="58679-123">HTTP アドレスからの XML ドキュメントを追加するには、クリックして**Web から追加**します。</span><span class="sxs-lookup"><span data-stu-id="58679-123">To add an XML document from an HTTP address, click **Add from Web**.</span></span>  
  
    -   <span data-ttu-id="58679-124">コピーするか、ウィザードに、XML ドキュメントの内容を入力、クリックして**の入力または貼り付け XML**します。</span><span class="sxs-lookup"><span data-stu-id="58679-124">To copy or type the contents of an XML document into the wizard, click **Type or paste XML**.</span></span>  
  
5.  <span data-ttu-id="58679-125">XML スキーマ セットを推論 をクリックするすべての XML ドキュメントのソースを指定した**ok** XML スキーマの推論に設定します。</span><span class="sxs-lookup"><span data-stu-id="58679-125">When you have specified all the XML document sources from which you want to infer the XML schema set, click **OK** to infer the XML schema set.</span></span> <span data-ttu-id="58679-126">スキーマ セットは、1 つ以上の XSD ファイルで、プロジェクト フォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="58679-126">The schema set is saved in your project folder in one or more XSD files.</span></span> <span data-ttu-id="58679-127">(各 XML 名前空間のスキーマ内のファイルが作成されます。)</span><span class="sxs-lookup"><span data-stu-id="58679-127">(For each XML namespace in the schema, a file is created.)</span></span>  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-schema-inference-in-the-visual-studio-xml-editor"></a><span data-ttu-id="58679-128">Visual Studio XML エディターでスキーマの推論を使用して、XML ファイルの XSD スキーマ ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="58679-128">To create an XSD schema file for an XML file by using schema inference in the Visual Studio XML Editor</span></span>  
  
1.  <span data-ttu-id="58679-129">Visual Studio XML デザイナーでの XML ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="58679-129">Edit the XML file in the Visual Studio XML Designer.</span></span>  
  
2.  <span data-ttu-id="58679-130">XML ファイルにカーソルがどこかにあるときに、 **XML**メニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="58679-130">When the cursor is somewhere in the XML file, the **XML** menu appears.</span></span> <span data-ttu-id="58679-131">をクリックして**Create Schema**上、 **XML**メニュー。</span><span class="sxs-lookup"><span data-stu-id="58679-131">Click **Create Schema** on the **XML** menu.</span></span> <span data-ttu-id="58679-132">XSD ファイルは、XML ファイルから推論された XSD スキーマから作成されます。</span><span class="sxs-lookup"><span data-stu-id="58679-132">An XSD file is created from XSD schema inferred from the XML file.</span></span>  
  
3.  <span data-ttu-id="58679-133">XSD スキーマ ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="58679-133">Save the XSD schema file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="58679-134">別の XSD スキーマは、同じスキーマを使用するためのものでは複数の XML ドキュメントから推論することがあります。</span><span class="sxs-lookup"><span data-stu-id="58679-134">Different XSD schemas might be inferred from multiple XML documents that are intended to have the same schema.</span></span> <span data-ttu-id="58679-135">これは、1 つの XML ファイルでは、特定の要素と属性が見つかったときに、または要素が次に例を異なる順序で含まれる場合に発生することができます。</span><span class="sxs-lookup"><span data-stu-id="58679-135">This can occur when particular elements and attributes are found in one XML file and not in another, or when elements are included in different order, for example.</span></span> <span data-ttu-id="58679-136">XSD スキーマの推論を使用する場合は、間違いがないため推論された XSD スキーマを確認してください。</span><span class="sxs-lookup"><span data-stu-id="58679-136">You should review inferred XSD schemas for completeness and accuracy when you use XSD schema inference.</span></span>  
  
#### <a name="to-include-an-xsd-schema-file"></a><span data-ttu-id="58679-137">XSD スキーマ ファイルを追加するには</span><span class="sxs-lookup"><span data-stu-id="58679-137">To include an XSD schema file</span></span>  
  
-   <span data-ttu-id="58679-138">既定では、Visual Basic プロジェクトで XSD ファイルを参照してくださいことはできません。</span><span class="sxs-lookup"><span data-stu-id="58679-138">By default, you cannot see XSD files in Visual Basic projects.</span></span> <span data-ttu-id="58679-139">XSD ファイルがプロジェクトのフォルダーに既に含まれている場合はクリックして、 **すべてのファイル**ボタン**ソリューション エクスプ ローラー**します。</span><span class="sxs-lookup"><span data-stu-id="58679-139">If your XSD file is already included in the folders for your project, click the **Show All Files** button in **Solution Explorer**.</span></span> <span data-ttu-id="58679-140">XSD ファイルを探し**ソリューション エクスプ ローラー**、ファイルを右クリックし、クリックして、**プロジェクトにインクルード ファイル**します。</span><span class="sxs-lookup"><span data-stu-id="58679-140">Locate the XSD file in **Solution Explorer**, right-click the file, and click **Include File in Project**.</span></span>  
  
-   <span data-ttu-id="58679-141">かどうかは、XSD ファイルされていない場合、プロジェクトの一部**ソリューション エクスプ ローラー**をポイントし、XSD ファイルを格納するフォルダーを右クリックして**追加**、クリックして**既存項目の**です。</span><span class="sxs-lookup"><span data-stu-id="58679-141">If your XSD file is not already part of your project, in **Solution Explorer**, right-click the folder in which you want to store the XSD file, point to **Add**, and then click **Existing Item**.</span></span> <span data-ttu-id="58679-142">XSD ファイルを見つけて、クリックして**追加**します。</span><span class="sxs-lookup"><span data-stu-id="58679-142">Locate your XSD file and then click **Add**.</span></span>  
  
#### <a name="to-import-an-xml-namespace-in-a-code-file"></a><span data-ttu-id="58679-143">コード ファイルで XML 名前空間をインポートするには</span><span class="sxs-lookup"><span data-stu-id="58679-143">To import an XML namespace in a code file</span></span>  
  
1.  <span data-ttu-id="58679-144">XSD スキーマからターゲットの名前空間を識別します。</span><span class="sxs-lookup"><span data-stu-id="58679-144">Identify the target namespace from your XSD schema.</span></span>  
  
2.  <span data-ttu-id="58679-145">コード ファイルの先頭に追加、`Imports`ターゲット XML 名前空間は、次の例で示すようにステートメントです。</span><span class="sxs-lookup"><span data-stu-id="58679-145">At the beginning of the code file, add an `Imports` statement for the target XML namespace, as shown in the following example.</span></span>  
  
     <span data-ttu-id="58679-146">[!code-vb[VbXMLSamples&#1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="58679-146">[!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_1.vb)]</span></span>  
  
     <span data-ttu-id="58679-147">既定の名前空間と XML 名前空間をインポートするには、XML 要素と名前空間プレフィックスがない属性に適用されている名前空間を追加、`Imports`ターゲット既定の XML 名前空間のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="58679-147">To import an XML namespace as the default namespace, that is, the namespace that is applied to XML elements and attributes that do not have a namespace prefix, add an `Imports` statement for the target default XML namespace.</span></span> <span data-ttu-id="58679-148">名前空間プレフィックスを指定しません。</span><span class="sxs-lookup"><span data-stu-id="58679-148">Do not specify a namespace prefix.</span></span> <span data-ttu-id="58679-149">次の例に示します、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="58679-149">Following is an example of an `Imports` statement.</span></span>  
  
     <span data-ttu-id="58679-150">[!code-vb[VbXmlSamples #&50;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="58679-150">[!code-vb[VbXmlSamples#50](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_2.vb)]</span></span>  
  
#### <a name="to-import-an-xml-namespace-for-all-files-in-a-project"></a><span data-ttu-id="58679-151">プロジェクト内のすべてのファイルの XML 名前空間をインポートするには</span><span class="sxs-lookup"><span data-stu-id="58679-151">To import an XML namespace for all files in a project</span></span>  
  
1.  <span data-ttu-id="58679-152">コード ファイルにインポートされた XML 名前空間は、そのコード ファイルのみに適用されます。</span><span class="sxs-lookup"><span data-stu-id="58679-152">An XML namespace imported in a code file applies to that code file only.</span></span> <span data-ttu-id="58679-153">プロジェクト内のすべてのコード ファイルに適用される XML 名前空間をインポートするには、ダブルクリックすると、プロジェクト デザイナーを開き**My Project**で**ソリューション エクスプ ローラー**します。</span><span class="sxs-lookup"><span data-stu-id="58679-153">To import an XML namespace that applies to all code files in a project, open the Project Designer by double-clicking **My Project** in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="58679-154">**参照**] タブの [、**インポートされた名前空間**ボックスに、完全な XML 名前空間宣言の形式でターゲットの XML 名前空間を入力 (たとえば、 `<xmlns: ns="http://sampleNamespace">`)。</span><span class="sxs-lookup"><span data-stu-id="58679-154">On the **References** tab, in the **Imported namespaces** box, type the target XML namespace in the form of a full XML namespace declaration (for example, `<xmlns: ns="http://sampleNamespace">`).</span></span> <span data-ttu-id="58679-155">ターゲットの XML 名前空間が名前空間プレフィックスを指定しない場合、名前空間は、プロジェクトの既定の XML 名前空間になります。</span><span class="sxs-lookup"><span data-stu-id="58679-155">If the target XML namespace does not specify a namespace prefix, the namespace will be the default XML namespace for the project.</span></span>  
  
3.  <span data-ttu-id="58679-156">クリックして**ユーザー インポートの追加**します。</span><span class="sxs-lookup"><span data-stu-id="58679-156">Click **Add User Import**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58679-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="58679-157">See Also</span></span>  
 <span data-ttu-id="58679-158">[Imports ステートメント (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="58679-158">[Imports Statement (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span></span>  
<span data-ttu-id="58679-159"> [[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="58679-159"> [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="58679-160"> [Visual Basic における XML IntelliSense](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)</span><span class="sxs-lookup"><span data-stu-id="58679-160"> [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)</span></span>

