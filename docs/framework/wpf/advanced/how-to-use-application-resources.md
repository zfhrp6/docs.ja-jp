---
title: "方法: アプリケーション リソースを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application resources [WPF]
- resources [WPF], application resources
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bac1fa1576e684a4b10f00310c08e4e7101a5df0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-application-resources"></a>方法: アプリケーション リソースを使用する
この例では、アプリケーション リソースを使用する方法を示します。  
  
## <a name="example"></a>例  
 次の例は、アプリケーション定義ファイルを示しています。 アプリケーション定義ファイルは、リソース セクションを定義します (値を<xref:System.Windows.Application.Resources%2A>プロパティ)。 アプリケーション レベルで定義されているリソースには、そのアプリケーションの一部であるその他すべてのページからアクセスできます。 この例では、リソースは宣言済みのスタイルです。 この例は省略内で定義されているコントロールのテンプレートをコントロール テンプレートを含む完全なスタイル指定できますが、時間がかかるため、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>スタイルのプロパティ set アクセス操作子。  
  
 [!code-xaml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xaml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 次の例は、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]前の例で定義されているアプリケーション レベル リソースを参照するページ。 使用して、リソースが参照されている、 [StaticResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)要求されたリソースの一意のリソース キーを指定します。 "GelButton" というキーを持つリソースが、現在のページで見つからないため、要求されているリソースのリソース ルックアップ スコープは、現在のページを越えて、定義されているアプリケーション レベルのリソースまで継続されます。  
  
 [!code-xaml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## <a name="see-also"></a>参照  
 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [アプリケーション管理の概要](../../../../docs/framework/wpf/app-development/application-management-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
