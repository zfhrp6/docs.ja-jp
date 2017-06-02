---
title: "方法 : ローカライズ可能アプリケーションでリソースを使用する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アプリケーション, ローカライズ可能"
  - "ローカライズ可能なアプリケーション"
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : ローカライズ可能アプリケーションでリソースを使用する
ローカリゼーションとは、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を異なるカルチャに適合させることを意味します。  そのためには、タイトル、キャプション、リスト ボックス項目などのテキストを翻訳する必要があります。  翻訳しやすいように、翻訳が必要な項目はリソース ファイルにまとめられています。  ローカライゼーション用のリソース ファイルの作成方法については、「[アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)」を参照してください。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションをローカライズ可能にするには、ローカライズ可能なすべてのリソースをリソース アセンブリに組み込む必要があります。  リソース アセンブリはさまざまな言語にローカライズされ、分離コードがリソース管理 [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] を使用して読み込みます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションに必要なファイルの 1 つはプロジェクト ファイル \(.proj\) です。  プロジェクト ファイルには、アプリケーションで使用するすべてのリソースを含める必要があります。  そのコード例を次に示します。  
  
## 使用例  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 アプリケーションでリソースを使用するには、<xref:System.Resources.ResourceManager> をインスタンス化し、使用するリソースを読み込みます。  その方法を次に示します。  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]