---
title: "方法 : アプリケーション リソースを使用する | Microsoft Docs"
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
  - "アプリケーション リソース"
  - "リソース, アプリケーション リソース"
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : アプリケーション リソースを使用する
アプリケーション リソースを使用する方法を次の例に示します。  
  
## 使用例  
 次の例では、アプリケーション定義ファイルを示します。  アプリケーション定義ファイルでは、リソース セクション \(<xref:System.Windows.Application.Resources%2A> プロパティの値\) が定義されています。  アプリケーション レベルで定義されているリソースには、そのアプリケーションの一部であるその他すべてのページがアクセスできます。  この例では、リソースは宣言済みのスタイルです。  コントロール テンプレートを含む完全なスタイルは長くなる場合があるので、この例では、スタイルの <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> プロパティの setter で定義されているコントロール テンプレートは省略してあります。  
  
 [!code-xml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 次の例では、前の例で定義されているアプリケーション レベルのリソースを参照する [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページを示します。  リソースを参照するには、要求するリソースの一意のリソース キーを指定する [StaticResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) を使用します。  "GelButton" というキーを持つリソースが現在のページには見つからないので、要求されているリソースのリソース ルックアップ スコープは、現在のページを越えて、定義されているアプリケーション レベルのリソースまで継続されます。  
  
 [!code-xml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## 参照  
 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [アプリケーション管理の概要](../../../../docs/framework/wpf/app-development/application-management-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)