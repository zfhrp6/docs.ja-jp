---
title: "SchemaImporterExtension の技術サンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f5eb78f-0ef6-433a-b095-3a63b1ce0bc9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 68e89053d1d4a36a0f015ed4e0082ae88e1de6a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="schemaimporterextension-technology-sample"></a><span data-ttu-id="1b0cb-102">SchemaImporterExtension の技術サンプル</span><span class="sxs-lookup"><span data-stu-id="1b0cb-102">SchemaImporterExtension Technology Sample</span></span>
[<span data-ttu-id="1b0cb-103">サンプルのダウンロード</span><span class="sxs-lookup"><span data-stu-id="1b0cb-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/SchemaImporterExtension.zip.exe)  
  
 <span data-ttu-id="1b0cb-104">このサンプルでは、XML スキーマをインポートするときのコード生成を微調整する、<xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> のカスタム化を示します。</span><span class="sxs-lookup"><span data-stu-id="1b0cb-104">This sample demonstrates a custom <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> that allows fine control over code generation when an XML schema is imported.</span></span> <span data-ttu-id="1b0cb-105">このアプリケーションは、この拡張機能のビルド、登録および起動の方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1b0cb-105">The application shows how to build, register and invoke this extension.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="1b0cb-106">コマンド プロンプトを使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="1b0cb-106">To build the sample using the command prompt</span></span>  
  
1.  <span data-ttu-id="1b0cb-107">コマンド プロンプト ウィンドウを開き、サンプルが格納されている、言語固有のサブディレクトリのいずれかに移動します。</span><span class="sxs-lookup"><span data-stu-id="1b0cb-107">Open a Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="1b0cb-108">コマンド ラインで「**msbuild.exe OrderSchemaImporterExtension.sln**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1b0cb-108">Type **msbuild.exe OrderSchemaImporterExtension.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="1b0cb-109">Visual Studio を使用してサンプルをビルドするには</span><span class="sxs-lookup"><span data-stu-id="1b0cb-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="1b0cb-110">[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]を開き、サンプルが格納されている、言語固有のサブディレクトリのいずれかに移動します。</span><span class="sxs-lookup"><span data-stu-id="1b0cb-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="1b0cb-111">OrderSchemaImporterExtension.sln ファイルのアイコンをダブルクリックして、このファイルを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="1b0cb-111">Double-click the icon for OrderSchemaImporterExtension.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="1b0cb-112">**[ビルド]** メニューの **[ソリューションのビルド]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1b0cb-112">On the **Build** menu, click **Build Solution**.</span></span>  
  
 <span data-ttu-id="1b0cb-113">アプリケーションは、既定の \bin ディレクトリまたは \bin\Debug ディレクトリにビルドされます。</span><span class="sxs-lookup"><span data-stu-id="1b0cb-113">The application will be built in the default \bin or \bin\Debug directory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="1b0cb-114">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="1b0cb-114">To run the sample</span></span>  
  
1.  <span data-ttu-id="1b0cb-115">コマンド プロンプトを使用して、新しい実行可能ファイルが格納されているディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="1b0cb-115">Navigate to the directory containing the new executable, using the command prompt.</span></span>  
  
2.  <span data-ttu-id="1b0cb-116">コマンド ラインで**実行ファイル名**を入力します。</span><span class="sxs-lookup"><span data-stu-id="1b0cb-116">Type **[exe name]** at the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b0cb-117">コメント</span><span class="sxs-lookup"><span data-stu-id="1b0cb-117">Remarks</span></span>  
 <span data-ttu-id="1b0cb-118">サンプルのバイナリ ファイルを作成する方法およびサンプルを登録する手順の詳細については、ソース コード ファイルおよび build.proj ファイル内のコメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b0cb-118">For more information about sample binary creation and registration steps, see the comments in the source code and build.proj files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b0cb-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b0cb-119">See Also</span></span>  
 <xref:System.CodeDom.CodeCompileUnit>  
 <xref:System.CodeDom.CodeNamespace>  
 <xref:System.CodeDom.CodeNamespaceImport>  
 <xref:Microsoft.CSharp.CSharpCodeProvider>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 <xref:System.Web.Services.Description>  
 <xref:System.Web.Services.Discovery>  
 <xref:System.Xml.Serialization>  
 <xref:System.Uri>  
 <xref:Microsoft.VisualBasic.VBCodeProvider>  
 <xref:System.Web.Services.Description.WebReference>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>
