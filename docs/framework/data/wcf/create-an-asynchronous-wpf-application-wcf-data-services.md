---
title: '方法: 非同期 Windows Presentation Framework アプリケーションを作成する (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
ms.openlocfilehash: d6acf3cbbfce491ebf98513b116d76ef9feb6d08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357635"
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a>方法: 非同期 Windows Presentation Framework アプリケーションを作成する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、データ サービスから取得したデータを Windows Presentation Framework (WPF) アプリケーションの UI 要素にバインドできます。 詳細については、次を参照してください。[コントロールへのデータ バインディング](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)です。により、アプリケーションのデータ サービス要求に応答を待機中に応答し続けるに非同期の方法でデータ サービスに対する操作を実行することもできます。 データ サービスに非同期でアクセスするには、Silverlight 用のアプリケーションが必要です。 詳細については、次を参照してください。[非同期操作](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)です。  
  
 このトピックでは、データ サービスに非同期でアクセスして、結果を WPF アプリケーションの要素にバインドする方法について説明します。 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 完了したときにこのサービスおよびクライアント データ クラスが作成された、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)です。  
  
## <a name="example"></a>例  
 次の XAML は、WPF アプリケーションのウィンドウを定義します。  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## <a name="example"></a>例  
 次の XAML ファイルの分離コード ページは、データ サービスを使用して非同期クエリを実行し、結果を WPF ウィンドウの要素にバインドします。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## <a name="see-also"></a>関連項目  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
